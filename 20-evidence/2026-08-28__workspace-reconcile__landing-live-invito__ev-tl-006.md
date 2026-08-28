---
id: ev-tl-006
client_id: thi-land
record_type: evidence
service_path: company
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/commit/dd7c8d271d71442a7efc776bae33ae84a91c7891
schema_version: 1.1.0
created_at: 2026-08-28
updated_at: 2026-08-28
---

# Landing riconciliata: il sorgente nel repo ora corrisponde al sito live (invito 24-25 ott)

## Il fatto

La versione live di thiland.ch (pre-apertura su invito 24-25 ottobre, CTA
"Mandami l'invito", form `invite-form`) **non esisteva in nessun branch** di
`thi-land-workspace`: `landing/index.html @ main` conteneva ancora la versione
"sconto" del 21/08 (commit `09016b0`, blob `c95794ee` identico su entrambi i
branch). Il sito e' quindi stato aggiornato con un deploy fuori pipeline, e il
check `production-state` fallisce dal 28/08 (run rosso delle 17:13).

Decisione di Alex: **vince il sito live** — il repo si riallinea al live, non
il contrario.

## Cosa e' stato fatto (PR #4 del workspace)

- Cattura byte-exact del live il 28/08: sha256
  `e9540ec45f1b7aa9522980b4354b896254ea3541673251f3966698b41bd937ee`
  (79.724 byte), doppia verifica indipendente (fetch browser + curl).
- Unica modifica prima del commit: `FORM_ENDPOINT` riportato al marker vuoto
  (`const FORM_ENDPOINT = "";`) perche' l'endpoint reale viene iniettato dal
  deploy — il repo non deve contenere l'URL dell'API.
- Committata come `landing/index.html` su branch `fix/landing-live-invito`
  (commit `dd7c8d2`), git blob verificato
  `0f38d4ac6245ff25eb98c7354ed46fb62aef4b33` = identico al file preparato.
- `ops/production-state.json` portato a v3 nello stesso commit: marker richiesti
  "Mandami l'invito", "24 e il 25 ottobre", "invite-form"; vietato
  "Voglio lo sconto". Nota: il form live si chiama `invite-form`, non
  `waitlist-form`.
- PR: https://github.com/spatialport/thi-land-workspace/pull/4 — al merge
  `deploy-landing.yml` rideploya la stessa pagina gia' live (no-op per gli
  utenti) e il check production-state torna verde.

## Contenuti live confermati nella cattura

Headline "Il 24 e il 25 ottobre pre-apertura su invito" · countdown al
24/10 09:00 · CHF 7 pre-apertura (bimbo + calzini + 1 adulto) · CHF 10/3 dal
31/10 · orari con THI Night sabato 9-22 · GA4 `G-NPCKC8BHP8` con Consent Mode
v2 · evento `generate_lead`.

## Implicazioni

- Chi ha deployato fuori pipeline il 21-28/08 va identificato solo per processo:
  d'ora in poi ogni modifica alla landing passa da `landing/index.html @ main`.
- Le varianti URL della landing per il message match con le ads (prossimo step)
  partono da questo sorgente riconciliato.

## Open questions

- Merge del PR #4: decisione di Alex (fa ripartire il deploy).
- Le tre versioni dell'offerta nel canon (aprile / deliverable / live) restano
  da riconciliare — il live e' l'autorevole (vedi ev-tl-005).
