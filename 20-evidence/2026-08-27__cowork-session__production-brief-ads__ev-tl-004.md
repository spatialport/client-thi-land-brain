---
id: ev-tl-004
client_id: thi-land
record_type: evidence
service_path: paid-media
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: spatial-port
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/commit/3fe7aeccb43ba0643c6a766345502087ef69aea4
schema_version: 1.1.0
created_at: 2026-08-27
updated_at: 2026-08-27
---

# Production brief ads — quante creatività, con che vincoli, con che calendario

Annesso operativo a ev-tl-003. Committato al workspace in
`fase-3-marketing-plan/production-brief-ads.md` (commit 3fe7aec).

## Conteggi decisi

- **2 creatività attive per ad set**, sempre: tutti gli ad set stanno sotto €20/giorno,
  e sotto quella soglia dividere il budget su 3-4 annunci rende nessuno leggibile al giorno 7.
- **14 asset totali** in 4 batch (consegne 31/08, 12/09, 26/09, 10/10), ognuno esportato
  in 4:5 e 9:16 = 28 file. Ritmo ~1,7 asset a settimana.
- Budget per fase, esatto: A €182 · B €189 · C €203 · D €187 = €761, riserva €89.

## Vincolo di frequenza — conseguenza strategica

€761 su ~3.000 adulti a CPM €15 = ~2,0 impression/persona/settimana: esattamente il
pavimento della banda small-audience. Ne discende che **la geo non può essere allargata**:
aggiungere Bellinzona città (+~8.000 adulti) porterebbe la frequenza a ~0,55/settimana,
cioè invisibili ovunque. Per una frequenza comoda (3,5/sett) servirebbero ~€1.450.

Conseguenza operativa sul targeting: **selezionare i comuni singolarmente**, mai un raggio
in km — un raggio di 8 km attorno a Lumino include Bellinzona e triplica il pubblico.

## Vincolo di produzione e regola etica adottata

Il parco è un cantiere fino a metà ottobre: le riprese interne (check-in, zona genitori,
arcade) non sono disponibili per i primi tre batch. È stata adottata una regola:
**non generare bambini fotorealistici con l'AI** per le inserzioni — policy Meta su minori
e contenuti sintetici, standard pubblicitari CH/UE sulla rappresentazione di minori, e
rischio diretto sulla proposta di valore (l'intera campagna vende fiducia dei genitori).
Stesso divieto per lo stock generico di parchi giochi.

Percorso alternativo definito per driver: TRUST su macro del braccialetto e motion graphic
della regola di uscita; CERTAINTY su pioggia/tipografia (nessuna persona in campo);
RELIEF su POV senza volti; countdown 100% grafico. La mascotte THI viene usata come firma
di brand, non come narratore, perché in questa campagna il compratore è il genitore.

## Strumenti di produzione verificati

FLORA: connettore attivo, workspace creata il 27/08. Il saldo NON è leggibile via API
(nessun endpoint di billing esposto; solo errore a runtime se il saldo USD è insufficiente)
— va letto nella UI. Listino visibile: 149 modelli immagine, 147 video. Stima per i 14
asset con 3 tentativi ciascuno: ~1.200 crediti se il modello image-to-video gratuito regge,
~5.100 con fallback a pagamento. HIGGSFIELD disponibile in alternativa con crediti già attivi.

## Open questions

- Saldo FLORA effettivo (da leggere in UI prima di pianificare la produzione).
- Esistono braccialetti campione fotografabili? (decisione tecnica gap #13 ancora aperta)
- Render dello spazio da Fase 1-2: quali sono utilizzabili come base creativa?
- Sezione sicurezza sulla landing per il message match TRUST: chi la implementa entro il 31/08?
