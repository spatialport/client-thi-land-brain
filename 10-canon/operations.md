---
id: thi-land-canon-operations
client_id: thi-land
record_type: knowledge
service_path: company
status: accepted
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: evidence://ev-tl-001
schema_version: 1.1.0
supersedes: thi-land-canon-operations@2026-08-19
created_at: 2026-08-11
updated_at: 2026-08-24
---
# Operations

Purpose: How the physical business actually works, including constraints, seasonality, locations and customer journey.

## Accepted knowledge

Physical venue:
- Upper floor of the Centro Opti, Lumino: play areas (soft play 3–6, arcade 7–10), reception, lockers (QR-opened via app), minimum 2 frequently checked bathrooms; lower floor: THI Kitchen/Restaurant, internally connected by stair/door — re-entry from restaurant to park only with an active wristband (THI-LAND-PROJECT.md).
- Max capacity ~100 people (children + parents); wood/plasterboard construction for acoustic insulation ("il minor rumore possibile") (THI-LAND-PROJECT.md).
- Access: motorway exit Bellinzona Nord 1 km, Castione station 1 km, bus stop 50–60 m, shared parking (THI-LAND-PROJECT.md).

Customer journey and access control:
- Check-in at reception with wristband + payment verification; mandatory parent↔child association; child exits ONLY with the associated adult; real-time occupancy monitoring with ~100 threshold and digital waitlist; automatic logging of entry/exit/duration; works offline with sync (THI-LAND-PROJECT.md; THI-LAND-OKKIO-CONTRATTO.md Appendice 1).
- Payments: cash + card (no cashless-only); arcade machines take CHF 1 coins; POS must integrate with the CRM; cash register system not yet selected (THI-LAND-PROJECT.md).
- Estimated footfall target: 35–40 children/day for the first 12 months (THI-LAND-PROJECT.md).

Software/systems (OKKIO, owned by the client per manifest exception):
- OKKIO is a single cloud application: staff/management interface, parent chatbot with the mascot's voice, automations and AI layer; privacy by design (data minimization for minors, NO facial recognition, data hosted EU/Switzerland) (THI-LAND-OKKIO-CONTRATTO.md Appendice 1).
- Contract SP-2026-THI-OKKIO-001 signed with KRISTAL SA, dated 15 June 2026; development start week of 6 July 2026; Phase 1 MVP (CRM & membership, access control & child safety, online tickets & birthdays, POS & compliant points system, partner video-feed integration, digital wallet card) due 15 September 2026; Phase 2 (marketing automation, AI email assistant, executive dashboard, parent chatbot, AI segmentation) starts with the launch campaign; Phase 3 (partner vision events via API, footfall forecasting, predictive marketing, loyalty optimizer) post-launch on real data (THI-LAND-OKKIO-CONTRATTO.md).
- Client-payable exclusions: hardware (RFID/NFC readers, wristbands, payment terminal, mini-PC, reception tablet — separate quote), network/electrical/internet, third-party running costs ~€100–300/month + usage, payment commissions (Stripe ~1.3–2.9% + ~€0.30), legal/fiscal advice; cameras/machine vision supplied by the client's partner, Spatial Port only integrates events via API (THI-LAND-OKKIO-CONTRATTO.md art. 7).
- Maintenance year 1 included (€1,500 value) with SLA: blocking issues taken up within 1 working day (THI-LAND-OKKIO-CONTRATTO.md art. 6).
- Wristband technology (RFID/NFC/QR) still an open technical decision, along with cameras, POS terminal and data residency (THI-LAND-OKKIO-CONTRATTO.md art. 2 note).

Spatial Port delivery infrastructure (internal):
- Project portal live at thiland.spatial-port.io (S3 private + OAC + CloudFront + ACM us-east-1 + Route53 spatial-port.io, marmareos pattern), with a collaborative PM dashboard whose tasks persist via Lambda Function URL + S3 pm-tasks.json (x-api-key header) (ISTRUZIONI-DEPLOY-THILAND-E-PM-BACKEND.md; 00-OVERVIEW-MARKETING-PLAN.md §2). Backends exist for waitlist (SES/Brevo), checkout, social and PM under projects/thi-land/backend/ (workspace audit). Credentials only via password-manager://spatial-port/thi-land/... and aws-secretsmanager://spatial-port/prod/thi-land/....
- Public landing: single landing at thiland.ch (00-OVERVIEW-MARKETING-PLAN.md changelog 5 Aug 2026); other domains reportedly bought: thiland.pro, thiland.swiss (to verify) (THI-LAND-PROJECT.md).

Operating constraints and compliance:
- **Opening hours — definitive, seven days a week, with staffing coverage (ev-tl-004, dec-tl-018).** These supersede the MASTER_PROMPT §6 schedule.

| Day | Hours | Minimum staff | Note |
|---|---|---|---|
| Mon | 15:00–19:00 | 1 | |
| Tue | 15:00–19:00 | 1 | |
| Wed | 09:00–13:00 | 1 | covered by hourly support |
| Wed | 13:00–19:00 | 2 | |
| Thu | 15:00–19:00 | 1 | |
| Fri | 15:00–18:00 | 1 | |
| Fri | 18:00–22:00 | 2 | evening support |
| Sat | 09:00–22:00 | 2 | THI Night |
| Sun | 09:00–19:00 | 2 | |

- Wednesday is the only split shift; its morning is the one slot with no permanent staff on site.
- Staffing model: two employees at 80% each (CHF 4,500 gross at 100%) plus 17 h/week of hourly support at CHF 25/h. Total staff cost CHF 124,755/year including 15% employer charges.
- Seasonality: weekday after-school vs full weekend days; summer = extended hours (THI-LAND-PROJECT.md).
- Legal: Swiss nLPD + GDPR; minors' data handled with parental consent; ticket-redemption arcade systems illegal in Switzerland → points system decoupled from arcade winnings; no facial recognition; client is data controller, Spatial Port processor (THI-LAND-PROJECT.md; THI-LAND-OKKIO-CONTRATTO.md art. 13).
- Key operational risks from discovery: cleanliness as reputational risk, drop-off legal/insurance complexity, finding qualified child-supervision staff, weekday/weekend and seasonal swings (THI-LAND-PROJECT.md §12).

## Open questions

- Cash register/POS selection and wristband technology — both still undecided and blocking OKKIO integration details.
- Confirm OKKIO Phase 1 delivery status vs the 15 September 2026 deadline (NXTO dashboard showed "Sistema punti & accessi" in progress as of June 2026, projects.ts).
- Drop-off operating model: approved or not; staffing/insurance requirements.
- Who operates day-to-day after opening (park manager not yet hired in sources)?
- Domain portfolio: verify ownership/status of thiland.ch, thiland.pro, thiland.swiss.
