---
id: ev-tl-008
client_id: thi-land
record_type: evidence
service_path: company
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/pull/6
schema_version: 1.1.0
created_at: 2026-08-28
updated_at: 2026-08-28
---

# Checkout Stripe diagnosticato e riparato (parte repo); resta un comando dal Mac

## Il guasto

Flusso e2e testato da Alex: landing -> email -> "Scelgo il mio turno" ->
biglietto.html -> "Prenota biglietto" NON apre Stripe. Diagnosi:

- biglietto.html live chiama POST /checkout (API wwjejejjj7) con
  {slot_id, quantity}; risposta: 502 {"error":"riserva_fallita"}.
- La Lambda in produzione e' una versione con turni+riserva MAI committata
  (altro deploy fuori pipeline); la riserva fallisce perche' manca la
  tabella DynamoDB dei turni (tutti i turni mostrano 30/30 = fallback).
- La chiave Stripe nella Lambda E' configurata e funziona (GET
  /checkout?session_id=... interroga Stripe davvero: 404 sessione_non_trovata).
- Il ruolo OIDC della CI ha solo S3/CloudFront: il backend non e' riparabile
  dalla pipeline, serve AWS CLI locale.

## Cosa e' stato shippato (PR #6, merge e607649, run verdi)

- landing/biglietto.html, grazie.html, privacy.html: capture byte-exact dal
  live, ora versionate e pubblicate da deploy-landing.yml (primo giro no-op).
- backend/checkout/lambda/handler.py riscritto: contratto identico al live
  (GET /turni, POST {slot_id,quantity} -> 409/{url}, GET summary), riserva
  ATOMICA su DynamoDB (mai overbooking), sessione Stripe CHF 7 con
  metadata.slot_id e scadenza 30 min, rilascio posto se Stripe fallisce.
- backend/checkout/fix-turni.sh: comando unico idempotente (tabella + seed
  condizionale 10 turni x 30 posti + permessi + update-function-code con env
  preservate + smoke test che restituisce il posto).
- Registro production-state v5: 11 superfici monitorate.

## Azione rimanente (bloccante per la vendita)

Dal Mac con credenziali AWS: `bash backend/checkout/fix-turni.sh`
Poi test reale: biglietto.html -> turno -> Prenota -> Stripe CHF 7.

## Limite accettato

Checkout abbandonato = posto trattenuto (no webhook): ripristino manuale
documentato in README-FIX.md; webhook checkout.session.expired come step
post-apertura.
