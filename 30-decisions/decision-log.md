---
id: thi-land-decision-log
client_id: thi-land
record_type: decision
service_path: company
status: accepted
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: client
sensitivity: confidential
source_ref: manual://decision-log
schema_version: 1.0.0
supersedes: thi-land-decision-log@2026-08-11
created_at: 2026-08-11
updated_at: 2026-08-21
---
# Decision Log

Append-only. Each revision supersedes the previous one; rows are never edited or removed.

| Decision ID | Date | Decision | Authority | Evidence | Consequence | Revisit trigger |
|---|---|---|---|---|---|---|
| dec-tl-001 | 2026-08-21 | THI RESTAURANT resta dentro SP-2026-THI-001 ma **solo per il logo**. Lavori ulteriori lo rendono un cliente a sé con fatturazione ad hoc. | alex-bellesia | ev-tl-002, ev-tl-003 | Il sub-brand non genera fattura separata oggi; nessun artwork applicato è coperto dal contratto attuale. | Prima richiesta di menù, insegna o packaging dal ristorante. |
| dec-tl-002 | 2026-08-21 | Il ristorante è gestito da un'**entità legale separata** da KRISTAL SA; identità da confermare, placeholder nel manifest. | alex-bellesia | ev-tl-003 | `ip_owner` e fatturazione del service path ristorante restano sospesi. | Identificazione dell'entità (task ev-tl-003-t4). |
| dec-tl-003 | 2026-08-21 | La **mascotte è esclusa** da THI RESTAURANT. L'omissione nel brandbook era voluta. | alex-bellesia | ev-tl-002, ev-tl-003 | Nessun materiale del ristorante può usare la mascotte, nemmeno sui menù bambini. | Richiesta esplicita del cliente di materiali baby al ristorante. |
| dec-tl-004 | 2026-08-21 | Il rapporto **70/30 rosso-verde è vincolante**, non indicativo. | alex-bellesia | ev-tl-002, ev-tl-003 | Verificabile in review: parti uguali = respinto. | Nuova palette o restyling del sub-brand. |
| dec-tl-005 | 2026-08-21 | Il nome pubblico della mascotte è **THI**. **OKKIO** resta il nome del solo software gestionale. | alex-bellesia | ev-tl-001, ev-tl-003 | Chiude il conflitto di naming; il brandbook (che dice OKKIO) va corretto. | — |
| dec-tl-006 | 2026-08-21 | La **licenza Arton è stata acquistata dal cliente** (art. 9.2, licenze premium a carico cliente). Copre il lettering riusato su THI RESTAURANT. | alex-bellesia | ev-tl-003 | Nessun blocco legale sulla produzione di insegne e packaging. | Estensione a un terzo marchio o a un nuovo licenziatario. |
| dec-tl-007 | 2026-08-21 | **KRISTAL SA non compare mai nei materiali pubblici**: è solo l'azienda che paga. Il nome pubblico è sempre THI LAND. | alex-bellesia | ev-tl-003 | Vincolo su ogni deliverable client-facing; `legal_name` resta metadato interno. | — |
| dec-tl-008 | 2026-08-21 | Agli adulti accompagnatori l'anteprima 24–25 ottobre è **gratuita**. *Assunzione di lavoro, da confermare con Daniele.* | alex-bellesia | ev-tl-003 | Coerente con «300 posti = 300 bambini» e con il claim famiglia 2+2 già pubblicato. Ricavo lordo anteprima CHF 2.100. | Conferma di Daniele (task ev-tl-003-t1). |
| dec-tl-009 | 2026-08-21 | Il tetto di **30 per turno conta solo i bambini**. Dieci turni × 30 = 300 bambini. | alex-bellesia | ev-tl-003 | Occupazione reale 60–80 persone per turno contro una capienza documentata di ~100. Margine sottile. | Verifica della capienza autorizzata del Centro Opti. |
| dec-tl-010 | 2026-08-21 | Costo unitario calzini antiscivolo: **CHF 1.00**. Margine netto per biglietto ≈ CHF 5.50 dopo commissioni Stripe. | alex-bellesia | ev-tl-003 | ~CHF 1.650 netti su 300 biglietti. L'offerta a CHF 7 con calzini inclusi è sostenibile. | Ripetizione dell'offerta dopo il 31 ottobre. |
| dec-tl-011 | 2026-08-21 | Sul software **prevale l'art. 12 del contratto OKKIO** (licenza perpetua, irrevocabile, non esclusiva, fino a 10 sedi) sull'art. 7 del contratto principale (trasferimento IP completo). | alex-bellesia | ev-tl-001, ev-tl-003 | Il codice sorgente **non** passa al cliente. `software_owner` nel manifest va corretto da `client` a `spatial-port` e l'eccezione descritta in CLAUDE.md decade. | Contestazione del cliente o appendice contrattuale firmata. |
| dec-tl-012 | 2026-08-21 | Divise, totem/insegna esterna e billboard 4×3 con QR: **approvati e in produzione**. Fase 1 chiusa. | alex-bellesia | ev-tl-003 | Nessuna azione residua sulla Fase 1 Brand. | — |
| dec-tl-020 | 2026-08-24 | Il numero **300 esce da tutto il copy pubblico**. La scarsità poggia su numero chiuso senza cifra e sul vincolo dei **30 bambini per turno**, comunicato come garanzia di qualità: si gioca senza calca. | alex-bellesia | ev-tl-005 | Landing, ads e social non citano più i 300 posti. Il vincolo resta vero e verificabile. | Cambio della capienza per turno. |
| dec-tl-019 | 2026-08-24 | Il funnel dell'anteprima si divide: **thiland.ch raccoglie email** per l'invito, l'acquisto vive su **biglietto.html**, raggiungibile solo dal link nella mail d'invito e non indicizzabile. | alex-bellesia | ev-tl-005 | ⚠️ Google Ads ottimizza ancora su `begin_checkout`, evento che la landing non emette più: serve una conversione `generate_lead` prima di continuare a spendere (task ev-tl-005-t1). Il prezzo CHF 7 resta visibile sulla landing per non tradire l'aspettativa nella mail. | Prime metriche reali di costo per lead. |
| dec-tl-018 | 2026-08-24 | Orari definitivi 7/7 dal Business Plan: Lun/Mar/Gio 15–19, Mer 09–19 (spezzato, mattina a supporto), Ven 15–22, Sab 09–22 (THI Night), Dom 09–19. | alex-bellesia | ev-tl-004 | Superano gli orari in canon da MASTER_PROMPT §6. Vanno su Google Business Profile, landing, brandbook e piano. | Cambio di copertura personale. |
| dec-tl-017 | 2026-08-24 | THI FOUNDER resta **fuori dalla landing** fino all'apertura del 31 ottobre; il funnel dell'anteprima vende solo il biglietto. | alex-bellesia | ev-tl-004 | Founder e abbonamenti arrivano col sito completo. Il BP li conta comunque (30/60/90 a CHF 350 una tantum). | Apertura del 31 ottobre 2026. |
| dec-tl-016 | 2026-08-24 | Abbonamenti: il livello base si chiama **THI STANDARD** (non START). Prezzi 49/69/99 CHF/mese; **THI FOUNDER CHF 350 una tantum**, non ricorrente. | alex-bellesia | ev-tl-004 | Chiude la domanda aperta su Founder (annuale vs una tantum). Da verificare le 4 card digitali di Fase 1, che potrebbero dire START. | Verifica artwork (task ev-tl-004-t1). |
| dec-tl-015 | 2026-08-24 | I calzini antiscivolo sono **inclusi in tutti e tre i pacchetti compleanno**, non solo in EXCLUSIVE. | alex-bellesia | ev-tl-004 | Coerente con la promessa «non devi portare nulla». Costo ~CHF 1/bambino, irrilevante sul margine del 72%. | Aumento del costo unitario calzini. |
| dec-tl-014 | 2026-08-24 | Sul listino ingressi **prevale il Business Plan**: bambino CHF 10 + adulto CHF 3. Decade il «CHF 10 a persona» del piano marketing v1.4 del 5 agosto. | alex-bellesia | ev-tl-004 | Landing, WP, Google Business Profile e brandbook vanno corretti. Ricavo medio per nucleo CHF 13. | Revisione del listino da parte del cliente. |
| dec-tl-013 | 2026-08-21 | I materiali pubblici restano **solo in italiano** fino a dopo l'apertura. L'adattamento DE/EN previsto dal contratto è un gap noto e accettato. | alex-bellesia | ev-tl-003 | Landing, social e Google Business Profile IT-only per anteprima e apertura. | Dopo il 31 ottobre 2026 (task ev-tl-003-t5). |
