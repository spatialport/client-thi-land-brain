---
id: ev-tl-011
client_id: thi-land
record_type: evidence
service_path: software
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/pull/7
schema_version: 1.1.0
created_at: 2026-09-07
updated_at: 2026-09-07
---

# Checkout biglietti spostato sull'account Stripe THILAND - Lumino; webhook vendite/posti attivo

## Source

Sessione Cowork del 07/09/2026 con Alex: switch account Stripe, deploy webhook dal Mac,
lettura del CSV pagamenti del vecchio account (ultime 4 settimane). PR #7 (merge 8c742b6)
e PR #8 (production-state v6) su thi-land-workspace.

## Redaction result

Nessun segreto: chiavi Stripe (restricted key `thiland-checkout-lambda`) e signing secret
del webhook stanno solo nelle env delle Lambda. Le email degli acquirenti restano nel CSV
in possesso di Alex e in Brevo, non in questo record.

## Factual summary

- **Account Stripe del checkout cambiato**: dal vecchio account "Residenza 3544" (quello
  che vendeva dal 29/08) al nuovo THILAND - Lumino (`acct_1L59ilAmQGObgs5G`): e' lo storico
  account delle prenotazioni studio della Residenza (pagamenti "studio - Reservation" dal
  2023), rinominato e destinato a T-Land da oggi in poi per decisione di Daniele.
- Nuovo Product/Price: "Biglietto pre-apertura THI LAND 24-25 ottobre", one-off, CHF 7.00
  IVA inclusa. Chiave: restricted key `thiland-checkout-lambda` (Checkout Sessions W,
  Payment Intents R, Refunds W, Charges R, Customers R).
- Switch eseguito con `backend/checkout/switch-stripe-account.sh` (aggiorna solo le due env
  Stripe della Lambda, preserva Brevo e il resto). Smoke test OK: sessione `cs_live` CHF 7.
- **Webhook Stripe attivo** (`backend/webhook/`, Lambda `thiland-stripe-webhook`, rotta
  `POST /webhook` sull'API wwjejejjj7, endpoint Stripe `we_1UCzHnAmQGObgs5GI30rQEkh`):
  `checkout.session.completed` -> DynamoDB `thiland-acquisti` + Brevo lista 4 + GA4 MP
  (GA4 non ancora configurato); `checkout.session.expired` -> posti restituiti al turno.
  Firma verificata, idempotente. In live non esiste "Send test event": test reale in corso
  con una sessione creata alle 12:05 CEST su dom-1700, scadenza 12:35.
- **Vecchio account (CSV 29 righe, tutte THI LAND, dal 29/08)**: 12 acquirenti paganti =
  20 posti = CHF 140; 3 rimborsi (2 test Alex, 1 cliente); 14 checkout abbandonati = 21
  posti. I biglietti pagati restano validi. I contatori `thiland-turni` letti alle 12:05
  mostrano esattamente 20 posti occupati (sab-1500: 8, sab-1700: 7, dom-1300: 3,
  dom-1500: 2), coerenti con i pagati: gli abbandonati risultano gia' rilasciati.
- Script `reconcile-old-account.sh` consegnato ad Alex (non nel repo): legge le sessioni del
  vecchio account con chiave read-only, riallinea i contatori a 30 - pagati per turno e
  fa il backfill dei 12 acquirenti in Brevo.
- Checkout live verificato dallo screenshot: nome pubblico ancora "Consorzio Daniele
  Pronzini / Fabio Dondi / Luca Merlo", EUR preselezionato (Adaptive pricing on), TWINT
  assente, Bancontact/EPS presenti. TWINT in attivazione, in attesa di Daniele.

## Direct implications

- La vendita gira sul nuovo account da oggi; i 12 acquirenti del vecchio account non sono
  visibili da `grazie.html` ne' dal webhook: la lista completa acquirenti = CSV vecchio
  account + `thiland-acquisti`.
- Chi paga e chiude la scheda viene ora registrato lo stesso (webhook); il CPA delle ads
  smette di essere falsato dal ritorno su grazie.html.
- Restano da chiudere sulla Dashboard: public business name, adaptive pricing off, TWINT
  on / Bancontact-EPS off.

## Candidate tasks

- Alex: Settings > Business > Public details > "THI LAND"; Adaptive pricing off; TWINT on.
- Alex: eseguire `reconcile-old-account.sh` (dry-run poi reale) e cancellare la chiave
  read-only del vecchio account.
- Configurare GA4 Measurement Protocol (GA4_MEASUREMENT_ID + API secret) e passare
  `metadata.ga_client_id` dal checkout, per attribuire il purchase server-side.
- Registrare la superficie `webhook` (Lambda + endpoint Stripe) in production-state con
  un check di salute.

## Candidate decisions

- Account Stripe di riferimento per T-Land: THILAND - Lumino (`acct_1L59ilAmQGObgs5G`),
  deciso da Daniele il 07/09/2026.

## Candidate canon

- operations: pagamenti biglietti su Stripe THILAND - Lumino; fonte di verita' delle
  vendite = DynamoDB `thiland-acquisti` (dal 07/09) + export vecchio account per il 29/08-06/09.
- channels: lista Brevo 4 = acquirenti biglietto pre-apertura.
