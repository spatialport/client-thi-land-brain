---
id: ev-tl-013
client_id: thi-land
record_type: evidence
service_path: software
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/pull/11
schema_version: 1.1.0
created_at: 2026-09-08
updated_at: 2026-09-08
---

# Honeypot della landing riempito dall'autofill di Chrome: iscrizioni scartate come bot

## Source

Test di Andrea (madstudio) dell'08/09/2026 con DevTools aperti, segnalato da Alex: "non sempre
parte la mail". Screenshot dei payload di due POST /iscrizione consecutivi.

## Redaction result

Email di test non riportate.

## Factual summary

- Il form invito di `landing/index.html` aveva un campo honeypot `email_address_check` (nascosto
  off-screen, con label "Non compilare", `autocomplete=off`). La Lambda waitlist, se il campo e'
  pieno, risponde 200 e scarta l'iscrizione (pattern Vitalis).
- Chrome ignora `autocomplete=off` e, vedendo "email" nel nome del campo, lo riempie con l'email salvata
  dell'utente quando si usa l'autocompilazione. Risultato: la landing mostra "Fatto: il tuo invito e'
  gia' partito", ma non parte niente e il lead non viene salvato.
- Riproduzione: primo invio compilato a mano -> honeypot vuoto -> invito partito; secondo invio con
  autofill -> honeypot = email personale salvata -> scartato.
- Fix (PR #11, mergiata, deploy landing automatico): input rinominato `tl_x7q`, senza label, con
  `data-lpignore` / `data-1p-ignore` / `data-form-type=other`. Il JSON verso la Lambda resta
  `email_address_check`: backend invariato.
- Non e' quantificabile quanti lead sono stati persi dal lancio della landing: la Lambda non logga gli
  scarti. Stima possibile: GA4 `generate_lead` (inviato comunque dal frontend) vs. iscrizioni reali.

## Direct implications

- Fino all'08/09 una quota rilevante dei visitatori Chrome desktop (autofill attivo) non ha ricevuto
  l'invito pur vedendo il messaggio di successo. Incide sul CPL reale delle ads e sul conversion rate
  lead -> biglietto osservato finora.
- Lo stesso pattern honeypot "email_address_check" arriva da Vitalis: da verificare anche li'.

## Candidate tasks

- Verifica post-deploy: iscrizione con autofill Chrome -> `email_address_check: ""` -> invito ricevuto.
- Stimare i lead persi (GA4 generate_lead vs DynamoDB/Brevo) e decidere se fare remarketing.
- Far loggare alla Lambda waitlist gli scarti honeypot (contatore CloudWatch) per non ripetere il buio.
- Controllare lo stesso campo sulla landing Vitalis.
