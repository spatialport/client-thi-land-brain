---
id: ev-tl-012
client_id: thi-land
record_type: evidence
service_path: software
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/pull/10
schema_version: 1.1.0
created_at: 2026-09-07
updated_at: 2026-09-07
---

# La Lambda checkout live non era il repo: webhook ricollegato, conferma biglietto funzionante (corregge ev-tl-011)

## Source

Sessione Cowork del 07/09/2026 pomeriggio con Alex: test di acquisto reale, log Brevo THI LAND
(csv 98 righe), codice vivo scaricato dalla Lambda `thiland-checkout` (29/08, 23 KB). PR #10
mergiata, PR #9 chiusa senza merge.

## Redaction result

Nessun segreto. Email acquirenti non riportate.

## Factual summary

- **Correzione a ev-tl-008, ev-tl-009 e ev-tl-011**: il `handler.py` del repo NON era il codice in
  produzione. La Lambda live (dal 29/08) ha: `POST /stripe-webhook`, tabella `thiland-prenotazioni`,
  hold 30 min con contatori `opzionati`/`venduti`, conferma via Brevo **transazionale** template #2
  (params TURNO, BAMBINI, IMPORTO, ORDINE), `POST /admin/prenotazioni` (elenco / sposta / rimborsa).
  `fix-turni.sh` non l'ha mai sovrascritta. Ora il codice live e' nel repo (PR #10).
- In Brevo THI LAND (account separato da Spatial Port/Vitalis) non esistono automazioni: template #1
  invito (double opt-in dalla Lambda waitlist), template #2 conferma (smtp/email dal webhook).
- Log Brevo: la conferma e' partita per tutti i paganti fino al 06/09 (ultima monteirokelly94, 21:18).
  Il test di Alex del 07/09 12:12 non l'ha ricevuta perche' gli eventi del nuovo account Stripe andavano
  al webhook duplicato creato la mattina (senza conferma), non al webhook della Lambda live.
- **Rimedio eseguito**: `rewire-stripe-webhook.sh` (signing secret del nuovo endpoint nella Lambda live,
  ritiro di Lambda `thiland-stripe-webhook`, rotta `POST /webhook`, ruolo e tabella `thiland-acquisti`,
  correzione opzionati dom-1700). Endpoint Stripe `we_1UCzHn...` puntato a `/stripe-webhook`.
  Resend dell'evento delle 12:12: 200, conferma ricevuta da Alex.
- Modello dati live: `metadata.slot_id` + `metadata.qty` (non `quantity`); fonte di verita' vendite =
  `thiland-prenotazioni` stato `pagata`.
- PR #9 (email biglietto con QR, aperta da una sessione parallela) chiusa: basata sul webhook duplicato
  e su `fix-turni.sh`, avrebbe sovrascritto la Lambda live.

## Direct implications

- Il funnel completo (lead -> invito -> biglietto -> Stripe THILAND - Lumino -> conferma) e' operativo.
- `deploy-checkout.sh` e `fix-turni.sh` (step codice) non vanno usati senza allinearli alle env live
  (ADMIN_TOKEN, PRENOTAZIONI_TABLE, BREVO_CONFERMA_TEMPLATE_ID, STRIPE_WEBHOOK_SECRET).
- La conferma viene inviata a ogni pagamento (transazionale): chi ricompra la riceve di nuovo.

## Candidate tasks

- Alex: rimborsare i test del 07/09 e liberare i posti (azione `rimborsa` dell'admin o comando DynamoDB).
- Alex: Dashboard Stripe: public business name "THI LAND", adaptive pricing off, TWINT on (attesa Daniele).
- Alex: `reconcile-old-account.sh` (aggiornare a `metadata.qty`) solo se i contatori non tornano.
- QR code nel biglietto: da fare nel handler live (_brevo_acquirente) + template #2.
- Allineare `deploy-checkout.sh` alle env live prima del prossimo deploy di codice.
- Canon: aggiornare ev-tl-008 ("non esiste webhook") e ev-tl-009 ("conferma non agganciata"): entrambe false.

## Candidate canon

- operations: backend biglietti = Lambda `thiland-checkout` con rotte /turni, /checkout, /stripe-webhook,
  /admin/prenotazioni; vendite in `thiland-prenotazioni`; conferma Brevo THI LAND template #2.
