---
id: ev-tl-005
client_id: thi-land
record_type: evidence
service_path: paid-media
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: spatial-port
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/commit/ea53e6a4eea00c1b1ed2d0c5549af160ea941a27
schema_version: 1.1.0
created_at: 2026-08-27
updated_at: 2026-08-27
---

# Correzione sostanziale: il funnel e' raccolta email, non vendita biglietto

Supera ev-tl-003 e ev-tl-004 sui punti che dipendevano dall'acquisto.

## Il fatto

Il commit `09016b0` del 21/08 sul workspace (*"landing: da vendita biglietto a
raccolta email con sconto esclusivo apertura"*) ha convertito la landing da
checkout a form email, con GA4 da `begin_checkout` a `generate_lead`. Il sito
live verificato il 27/08 lo conferma:

- Headline: "Il 24 e il 25 ottobre pre-apertura su invito."
- CTA: "Mandami l'invito" (form email, nessun acquisto in pagina)
- Pre-apertura 24-25 ott: CHF 7, include bimbo + calzini antiscivolo + 1 adulto
- Apertura pubblica 31 ott: CHF 10 bimbo / CHF 3 adulto

## Cosa e' stato ricalcolato

- **Obiettivo campagna Meta**: da Vendite/Purchase a **Contatti/`generate_lead`**.
- **Metriche**: da "300 biglietti a CPA 3,33 EUR" a **450-500 email a CPL target
  1,70 EUR**, con conversione email->biglietto ~40% misurata a valle (~180-200
  biglietti attesi dalle ads; il resto dal layer organico).
- **CTA di ogni creativita'**: da "Prenota ora" a "Mandami l'invito" / bottone
  Meta "Iscriviti".
- **Prezzi citati**: CHF 7 pre-apertura e CHF 10 apertura (non CHF 7 vs 15).
- **Ordine dei driver**: STATUS ("Solo su invito") diventa il primo test cold,
  perche' cio' che compra l'email e' la ricompensa per averla lasciata. TRUST
  (braccialetto, uscita protetta) e' spostato su sequenza email e step acquisto:
  e' un driver da decisione di visita, e soprattutto la landing non lo nomina,
  quindi mancherebbe il message match. Torna testabile al freddo solo se entro
  il 12/09 la landing riceve una sezione dedicata.
- **Aggiunta la sequenza email** (4 email), assente nella v1 e ora sul percorso
  critico: con un funnel lead sono le email a chiudere, non le ads.

## Token di brand recuperati (da deliverables/landing.html)

teal `#006a61` / teal-light `#008378` / teal-pale `#e0f5f2` / lime `#b2f746` /
orange `#FF5500` / dark `#191c1e` / surface `#f7f9fb`. Font: **Outfit** (200-800).
Tagline: "Dove l'energia diventa gioia." Logo `thi-logo.svg` (mascotte + wordmark).
Render disponibili in `strategy-assets.js`: entrance-hero, children-playing,
parent-lounge, birthday-party, reading-corner, restaurant, night-exterior,
piu' hero-video.mp4.

## Tre versioni dell'offerta in circolazione (da riconciliare nel canon)

1. Canon aprile: Founder 100 posti a ~CHF 250.
2. `deliverables/landing.html`: Open Day, CHF 5 vs 12, Founder CHF 350/anno.
3. **Sito live (autorevole)**: pre-apertura su invito 24-25 ott, CHF 7; apertura
   pubblica 31 ott, CHF 10 / CHF 3.

## Sovrapposizione rilevata con la Fase 3 esistente

`fase-3-marketing-plan/` contiene gia' 16 documenti di piano marketing, fra cui
`07-piano-adv-meta-google-tiktok.md`, `09-strategia-email-marketing.md`,
`13-budget-canali.md` e `14-campagna-google-ads.md`. I due documenti aggiunti in
questa sessione (`ads-strategy-anteprima.md`, `production-brief-ads.md`) coprono
lo sprint pre-apertura da EUR 1.000 e vanno **riconciliati** con quei piani:
altrimenti convivono due piani adv paralleli. Decisione da prendere.

## Open questions

- La sequenza email esiste gia' in `09-strategia-email-marketing.md`? Se si',
  va allineata al funnel invito, non riscritta.
- Chi possiede la riconciliazione fra i due piani adv?
- Sezione sicurezza sulla landing entro il 12/09: si' o no (sblocca TRUST cold).
- Saldo FLORA (non leggibile via API, da UI).
