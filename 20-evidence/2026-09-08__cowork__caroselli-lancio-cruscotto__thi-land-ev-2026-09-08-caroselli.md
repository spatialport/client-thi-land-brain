---
id: thi-land-ev-2026-09-08-caroselli
client_id: thi-land
record_type: evidence
service_path: content
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/commit/9fce1aa0208a272b9d755653c467b20263627206
schema_version: 1.1.0
created_at: 2026-09-08
updated_at: 2026-09-08
---

# Due caroselli di lancio pubblicati sul cruscotto di validazione

## Cosa è stato prodotto

Due caroselli Instagram da 6 slide ciascuno (1080x1350, 4:5), costruiti sulla
strategia social THI LAND v1.1 e sul brand canon (teal #006A61, lime #B2F746,
arancio #FF5500, ambra #FBBF24; Outfit 800/500; logotipo sempre da file).

**Carosello 1 — «Le porte si aprono»** (anteprima 24-25 ottobre → apertura 31)

1. «Le porte si aprono.» — chip lime *24 e 25 ottobre · anteprima su invito*
2. «Qui dentro si corre, si vola, si ride.» — aree separate per età, 3-10 anni
3. «E c'è THI, che gioca con loro.» — la mascotte come compagno d'avventura
4. «Ogni bimbo ha il suo spazio.» — chip ambra *massimo 100 persone*
5. «Poi apriamo per tutti.» — chip arancio *31 ottobre · apertura*
6. End card — doppia data, CTA thiland.ch, Centro OPTI

**Carosello 2 — «CHF 7. Dentro ce ne sono 15.»** (scomposizione del biglietto)

1. «CHF 7. Dentro ce ne sono 15.» — chip lime *24 e 25 ottobre · anteprima*
2. «L'ingresso al parco.» — chip *CHF 10*
3. «I calzini antiscivolo.» — chip *CHF 5*
4. «Insieme farebbero 15.» — chip ambra *separati: CHF 15*
5. «E i posti sono 300.» — chip arancio *300 posti*
6. End card — CHF 7 calzini inclusi, CTA thiland.ch

Slide 3 e 5 del secondo carosello non sono generate: sono frame del video di
lancio del cliente (calzino con marchio THI LAND; esterno del Centro OPTI).
Tutte le altre immagini sono generate in AI, quindi nessun bambino reale
compare nei creativi.

## Dove sono finite

Repo `thi-land-workspace`, branch `main`:

- 12 anteprime WebP in `deploy-aws/site/social-media/carosello-{porte,biglietto}-NN.webp`
- `deploy-aws/site/social-seed.json` e `social/social-seed.json` (byte-identici,
  blob `17e7b9751a60bf297f0cc537bc767594f58bbb1b`) con gli slot **18** (25/10) e
  **06** (01/10) ricablati sui nuovi `images[]`

Il workflow `deploy-portale` è passato; verificato in produzione su
`https://thiland.spatial-port.io/` — seed servito (22 803 byte) e tutte e 12 le
immagini rispondono 200 e decodificano come WebP.

**Nessuna caption è stata riscritta.** Lo slot 06 è stato scelto perché la sua
caption già approvata è esattamente la scomposizione CHF 10 + CHF 5 = 15 con
prezzo anteprima 7; lo slot 18 perché è il formato «Bonus — La giornata di
THI LAND».

## Semaforo

- Carosello 1: 🟢 verde — nessun volto reale, nessun dato sensibile.
- Carosello 2: 🟡 giallo — contiene prezzi e date; i numeri provengono dalla
  caption già presente nel seed, non sono stati inventati.

## Punti aperti

- Verificare la formulazione «bagni ogni 30 minuti» usata altrove nei materiali:
  il canon dice 30-60 minuti.
- Confermare che la landing thiland.ch raccolga le iscrizioni entro le date di
  pubblicazione dei post che rimandano al link in bio.
- I master a piena qualità (PNG 1080x1350) restano fuori dal repo: vanno su
  Instagram direttamente, il cruscotto usa solo le anteprime WebP leggere.
