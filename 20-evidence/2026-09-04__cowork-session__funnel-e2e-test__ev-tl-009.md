---
id: ev-tl-009
client_id: thi-land
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://www.thiland.ch/
schema_version: 1.1.0
created_at: 2026-09-04
updated_at: 2026-09-04
---

# Funnel lead -> acquisto camminato dal vivo: regge fino a Stripe, si rompe sul post-pagamento

## Source

Sessione Cowork del 04/09/2026: pull di `thi-land-workspace @ main` e del brain, piu' test
end-to-end reale su thiland.ch (lead di prova `alex+thitest@spatial-port.com`, sessione Stripe
aperta e abbandonata, nessun pagamento). Aggiorna ev-tl-008 sullo stato del checkout.

## Redaction result

Nessun segreto: chiavi Stripe e Brevo non compaiono; endpoint API gia' pubblici perche' chiamati
dalle pagine live. Il lead di test e' un indirizzo interno Spatial Port.

## Factual summary

- **Stadi 1-4 verificati e funzionanti.** Landing + 6 varianti (`/invito /denner /eta /gonfiabili
  /relax /pioggia`, tutte noindex). Form -> `POST /iscrizione` (API e044wtwvc7) -> upsert DynamoDB
  `thiland-waitlist`; GA4 `generate_lead` sparato. `biglietto.html` noindex; `GET /turni` risponde
  con disponibilita' reale: **`fix-turni.sh` risulta eseguito**, la tabella `thiland-turni` esiste
  e la Lambda ci scrive (non piu' il fallback 30/30 di ev-tl-008).
- **L'email di invito arriva davvero, in meno di 60 secondi**, da `info@thiland.ch`, oggetto "Il tuo
  invito per THI LAND", CTA verso `thiland.ch/biglietto.html`, copy corretto (CHF 7, calzini, un
  genitore compreso, under 2 gratis), unsubscribe presente. I link passano da `r.link.thiland.ch`:
  e' un'**automazione Brevo che non esiste nel repo** e non e' in `production-state.json`.
- **Il checkout apre Stripe**: `POST /checkout {slot_id, quantity}` -> riserva atomica -> sessione
  `cs_live` CHF 7.00. La vendita e' tecnicamente possibile: ev-tl-008 e' superato su questo punto.
- **Rotture critiche trovate:**
  1. Il checkout Stripe si presenta come **"Residenza 3544"**: la rinomina in "T-Land Lumino"
     concordata nella call del 26/08 non e' applicata sul branding pubblico dell'account.
  2. **Nessun webhook Stripe.** Al 04/09 risultano 19 posti impegnati su 300 (uno e' il test di
     questa sessione): non e' distinguibile dai nostri sistemi quanti siano vendite e quanti
     abbandoni. I contatori dei turni non sono affidabili come indicatore di riempimento.
  3. **TWINT assente** fra i metodi di pagamento (ci sono carta, Klarna, Bancontact ed EPS: gli
     ultimi due irrilevanti in CH) e **valuta preselezionata in EUR** (7,74 EUR) invece che CHF 7.
- **Rotture alte:** `purchase` GA4 e push nella lista acquirenti Brevo avvengono solo se l'utente
  torna su `grazie.html` dopo il pagamento — chi paga e chiude la scheda non viene tracciato ne'
  registrato, e il CPA delle ads ne risulta falsato. La notifica SES di nuovo lead ad Alex **non
  arriva** (verificato in casella): mittente non verificato o SES ancora in sandbox.
- **Rotture medie:** nessun `customer_email` prefill nella sessione Stripe, quindi lead e acquirente
  restano scollegati; della sequenza email prevista in ev-tl-005 risulta attiva solo l'email 1;
  `email/conferma-biglietto.html` esiste nel repo ma non e' agganciata a nulla.

## Direct implications

- Il blocco alla vendita segnalato in ev-tl-008 e' risolto: si compra. Il problema si e' spostato a
  valle, sulla fiducia al pagamento e sulla misurazione.
- Prima di qualsiasi comunicazione sulla disponibilita' dei turni va guardato Stripe: i 18 posti
  impegnati pre-test non sono attribuibili.
- L'automazione Brevo dell'invito e' oggi l'unico anello del funnel senza versionamento ne'
  copertura di `production-state`.

## Candidate tasks

- Rinominare l'account Stripe (dati pubblici dell'attivita') — Alex, bloccante.
- Attivare TWINT, rimuovere Bancontact/EPS, forzare `currency: chf` nella sessione — Alex.
- Webhook Stripe su `checkout.session.completed` e `checkout.session.expired`: restituisce i posti
  scaduti e registra la vendita server-side (GA4 Measurement Protocol + Brevo).
- Verificare il mittente/dominio in SES eu-central-1 e uscire dalla sandbox.
- Portare l'HTML dell'email di invito nel repo e registrarla come 12a superficie in
  `production-state.json`.
- Completare la sequenza email (recupero non-acquirenti, prova sociale, countdown).

## Candidate decisions

- Nessuna nuova decisione: il record fotografa lo stato del funnel al 04/09/2026.

## Candidate canon

- operations: il funnel di pre-apertura e' lead-gated (nessun link al checkout dalla landing;
  `biglietto.html` si raggiunge solo dal link dell'email di invito).
- channels: l'email di invito e la lista acquirenti sono gestite in Brevo; DynamoDB
  `thiland-waitlist` resta la fonte di verita' dei lead, Stripe quella degli acquisti.
