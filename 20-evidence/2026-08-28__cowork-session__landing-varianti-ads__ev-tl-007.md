---
id: ev-tl-007
client_id: thi-land
record_type: evidence
service_path: paid-media
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: spatial-port
access_scope: internal
sensitivity: internal
source_ref: https://github.com/spatialport/thi-land-workspace/pull/5
schema_version: 1.1.0
created_at: 2026-08-28
updated_at: 2026-08-28
---

# Sei varianti landing message-match per le ads, live e verificate

Approvazione di Alex in sessione ("shippiamo le variazioni e pushamole").
PR #5, merge 541fa8c2, deploy-landing verde, production-state verde su 8 superfici.

## Il principio

Ogni ad atterra su una pagina che continua il suo claim (regola del message
match): stessa landing invito, stesso form `invite-form`, stesso endpoint
iniettato dal deploy, stesso GA4 e countdown. Cambiano solo title, meta,
H1, hero-sub e la source di attribuzione.

## Mapping ad -> URL -> source

| Ad (creativita' in Drive/zip) | URL | H1 | source (DynamoDB/Brevo + GA4) |
|---|---|---|---|
| status-solo-invito (STATUS) | /invito | Il 24 e il 25 ottobre / si entra solo su invito. | landing-invito |
| local-sopra-il-denner (LOCALE) | /denner | Apre qui. / Sopra il Denner. | landing-denner |
| eta-piccoli-grandi (ETA') | /eta | I piccoli di qua. / I grandi di la'. | landing-eta |
| anti-gonfiabili (ANTI) | /gonfiabili | Niente gonfiabili / sporchi. | landing-gonfiabili |
| relief-tu-ti-siedi (RELIEF) | /relax | Loro giocano. / Tu ti siedi. | landing-relax |
| origine-sabato-piove (ORIGINE) | /pioggia | E' sabato mattina e piove... / ma il parco giochi e' sempre aperto. | landing-pioggia |

Base URL: https://www.thiland.ch (senza slash finale: oggetto S3 dedicato).
Tutte noindex con canonical sulla home. Homepage invariata byte-exact
(sha256 e9540ec4...37ee).

## Attribuzione a tre strati

1. `source: landing-<slug>` nel POST /iscrizione -> colonna source in
   DynamoDB e in Brevo (per-lead, sopravvive a qualsiasi cookie).
2. `lead_source` sull'evento GA4 `generate_lead` + page_path della variante.
3. UTM delle ads (utm_campaign=thi-invito-<driver>, utm_content=<creativita'>)
   invariate: la variante non le tocca.

## Pipeline estesa (deploy-landing.yml)

Iniezione endpoint su ogni `landing/*/index.html`; upload anche come oggetto
senza estensione (URL puliti senza redirect); invalidation `/*`; verifica
post-deploy del form su home + ogni variante. Registro production-state v4:
8 superfici monitorate ogni giorno.

## Note operative

- Il run production-state sullo stesso push del deploy puo' andare rosso per
  gara (controlla prima che il deploy finisca): si auto-risana al giro dopo.
  Issue #3 chiusa con questa spiegazione.
- Le ads vanno puntate all'URL della propria variante, NON alla home.
