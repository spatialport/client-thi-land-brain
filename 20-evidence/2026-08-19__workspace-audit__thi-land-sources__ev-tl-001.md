---
id: ev-tl-001
client_id: thi-land
record_type: evidence
service_path: company
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: "file:///Users/alexbellesia/Documents/Claude/Projects/NXTO/projects/thi-land/"
schema_version: 1.1.0
created_at: 2026-08-19
updated_at: 2026-08-19
---
# Evidence — Workspace audit of THI LAND primary sources

- Source: local workspace audit (Glob/Grep/Read) across /Users/alexbellesia/Documents/Claude/Projects/NXTO/, /Users/alexbellesia/Projects/, /Users/alexbellesia/Downloads/.
- Actors: Claude agent on behalf of Alex Bellesia (alex@spatial-port.com).
- Redaction: no secrets, passwords or API keys copied; Spatial Port contract economics kept out of canon bodies (referenced only in this internal evidence note where needed for conflicts). Credentials referenced only as password-manager://spatial-port/thi-land/... or aws-secretsmanager://spatial-port/prod/thi-land/....

## Discovered sources (read → used for canon)

Primary folder A — /Users/alexbellesia/Documents/Claude/Projects/NXTO/projects/thi-land/
- `_input/THI_LAND_Contratto_testo.txt` (+ PDF) — signed services contract SP-2026-THI-001 (19 Mar 2026): 8 phases, timeline, team, IP transfer on full payment, exclusions. READ.
- `MASTER_PROMPT_THILAND.md` — master brief with official client data (pricing, memberships, Founder waves, hours, brand tokens, mascot OKKIO). READ.
- `fase-3-marketing-plan/00-OVERVIEW-MARKETING-PLAN.md` — marketing plan overview v1.4 with 5 Aug 2026 changelog (final dates/prices, CHF 3,000 ADV budget, thiland.ch). READ.
- `fase-3-marketing-plan/02-posizionamento-differenziazione.md` — positioning source of truth: statement, claim, 4 pillars, tone do/don't. READ (first 120 lines).
- `fase-3-marketing-plan/01,03–15` — strategy, Founder campaign, birthdays, events, launch, ADV, social calendar (+xlsx), email, partnerships, PR, KPI dashboard, budget (+xlsx), Google Ads, Google Business Profile. Skimmed via overview index only.
- `presentazioni/` — HTML presentation hub (8 contract phases) + assets (thi-logo.svg, okkio-head.svg, GUIDA-PORTALE-THILAND.pdf). Not parsed.
- `backend/` (waitlist, checkout, social, pm) and `deploy-aws/` — serverless Lambdas and deploy scripts for landing/portal. Listed only.
- `MASTER_PROMPT_THILAND_REVISIONE.md`, `REVISIONE-CRITICA.md`, `QUALITY-GATE-REPORT.md`, `CONSEGNA-REPORT.md`, `IMPACT-STRATEGIA-OPENDAY.md`, `INVENTARIO-SECOND-BRAIN.md` — revision/QA/delivery reports. Not read (secondary).

Primary folder B — /Users/alexbellesia/Documents/Claude/Projects/NXTO/clienti/THI-LAND/
- `THI-LAND-PROJECT.md` — richest single source: discovery meetings 24+26 Mar 2026 (vision, values, competitors, catchment, personas, offer, space, team, risks, open decisions). READ.
- `THI-LAND-OKKIO-CONTRATTO.md` — OKKIO software contract SP-2026-THI-OKKIO-001 (15 Jun 2026) with KRISTAL SA (CHE-115.363.630): 3 phases, €21,960 total, licence art. 12, nLPD art. 13, functional spec appendix. READ.
- `THI-LAND-SOFTWARE-OKKIO-SPEC.md`, `THI-LAND-OKKIO-PIANO-SVILUPPO.md`, `THI-LAND-OKKIO-PREVENTIVO.md`, `THI-LAND-OKKIO-EMAIL-*.md` — OKKIO spec/dev plan/quote/emails. Not read (contract supersedes for canon).
- `THI-LAND-SPRINT-APRILE-2026.md`, `THI-LAND-GAP-ANALYSIS-TODO.md`, `THI-LAND-REPORT-SOCIAL-ADS.md`, `BRAND-BOOK-PLAN.md`, `BRAND-BOOK-V2-PLAN.md` — working docs. Not read.
- Site files, Arton-*.otf fonts, LOGO-1/LOGO-2/HEAD.svg, hero video, moodboards (per MASTER_PROMPT §3). Binaries, not parsed.

Other locations:
- `/Users/alexbellesia/Documents/Claude/Projects/NXTO/THI-LAND-BRAND-BOOK.html`, `THI-LAND-STRATEGIA-DIGITAL.html`, `THI-LAND-Merchandising-Prompts.md` — brandbook (token source), digital strategy deck, merch prompts (per MASTER_PROMPT §3). Not parsed; tokens taken from MASTER_PROMPT §5 pending verification.
- `/Users/alexbellesia/Projects/SITO SPATIALPORT/ISTRUZIONI-DEPLOY-THILAND-E-PM-BACKEND.md` — deploy runbook for thiland.spatial-port.io + PM dashboard S3/Lambda backend. READ (first 100 lines).
- `/Users/alexbellesia/Projects/NXTO-SPATIALPORT/src/data/projects.ts` — NXTO dashboard: Thi Land phases (brand done Jan 15–May 12 2026; site+ticket landing done Apr–May; points/access system May 15–Jul 15 in progress; launch+social Jun 1–Aug 31) and tasks (points spec, launch social plan, merch QC, waitlist→live tickets done). READ (thi-land section).
- `/Users/alexbellesia/Projects/NXTO-SPATIALPORT/src/data/finance.ts` — Thi Land invoice inv-2026-010 (CHF 12,800 paid, issued 2026-04-15) and project economics entry (CHF 48,000 value, 360h estimated / 402h actual). READ (thi-land lines; internal only, never in client deliverables).
- `/Users/alexbellesia/Projects/NXTO-SPATIALPORT/src/data/content.ts` — June 2026 Thi Land content items (mascot welcome post published, points-system promo, summer merch reel). READ (thi-land lines).
- `/Users/alexbellesia/Downloads/` — THILANDLOGO.png, THILAND LOGO.svg, FAVICONTHILAND.jpg, THILAND-OKKIO-CONTRATTO.docx/.pdf (binary duplicates of the MD contract). Listed only.

## Concise factual summary

THI LAND is an indoor play park for children 3–10 inside the Centro Opti, Lumino (Ticino, CH), founded by Daniele Pronzini & Verena (entity KRISTAL SA), named after their son Thiago. Positioned as the "boutique" alternative to big chaotic parks; claim «Dove l'energia diventa gioia». Spatial Port delivers 8 phases (brand, landing, marketing plan, website, OKKIO CRM/access/points software via separate contract, launch, social 12m, maintenance 12m). Preview/Open Day 24–25 Oct 2026 (300 tickets, CHF 7), public opening 31 Oct 2026 (CHF 10 entry). Founder campaign: 100 places (~70 realistic), waves 2–3 discounted. Campaign live from 28 July 2026.

## Direct implications

- Canon files 10-canon/{company,people,offer,icp,positioning,channels,operations,brand}.md filled as proposed knowledge from the above sources.
- Manifest active_service_paths populated (branding, content, crm, landing-pages, local-seo, paid-media, software).

## Candidate tasks

- Verify brand tokens directly against THI-LAND-BRAND-BOOK.html.
- Obtain written client decisions: Founder Wave 1 formula, birthday nomenclature/pricing, ADV geo, photo release validation, TikTok in/out.
- Confirm OKKIO Phase 1 MVP status vs 15 Sep 2026 deadline.

## Candidate decisions

- Reconcile software ownership language: manifest exception (software_owner: client) vs OKKIO art. 12 perpetual 10-site licence vs main contract art. 7 full IP transfer.
- Decide the ADV budget of record (CHF 3,000/~7 months vs ~€1,200/month contract-era).
- Decide the mascot's public name (OKKIO vs THI) — OKKIO also names the software.

## Candidate canon

- All facts flagged "Proposed knowledge" in 10-canon/*; promote after Alex's review.
