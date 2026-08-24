---
id: ev-tl-004
client_id: thi-land
record_type: evidence
service_path: company
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: "file:///Users/alexbellesia/Documents/Claude/Projects/NXTO/clienti/THI-LAND/THI-LAND-BUSINESS-PLAN-2026-08.xlsx"
schema_version: 1.1.0
created_at: 2026-08-24
updated_at: 2026-08-24
---
# Evidence — Business Plan with definitive hours, birthday packages and price list

- Source: `Business_Plan_THI_LAND_COMPLETO_con_Compleanni.xlsx`, supplied by the client and archived in the workspace as `clienti/THI-LAND/THI-LAND-BUSINESS-PLAN-2026-08.xlsx`. Nine sheets: Assunzioni, Personale, Scenari, Conto Economico, Break-even, Dashboard, Note, Compleanni, Abbonamenti.
- Actors: Daniele Pronzini / KRISTAL SA as the origin of the confirmed operating figures; Alex Bellesia as the authority accepting them into the brain (chat session, 24 August 2026).
- Redaction result: nothing removed. Financial projections are internal (`access_scope: internal`) and must never appear in client-facing deliverables — the same rule already applied to Spatial Port's own contract economics.

## Factual summary

### Opening hours — definitive, seven days a week

| Day | Hours | Minimum staff | Note |
|---|---|---|---|
| Monday | 15:00–19:00 | 1 | |
| Tuesday | 15:00–19:00 | 1 | |
| Wednesday | 09:00–13:00 | 1 | covered by hourly support |
| Wednesday | 13:00–19:00 | 2 | |
| Thursday | 15:00–19:00 | 1 | |
| Friday | 15:00–18:00 | 1 | |
| Friday | 18:00–22:00 | 2 | evening support |
| Saturday | 09:00–22:00 | 2 | THI Night |
| Sunday | 09:00–19:00 | 2 | |

These **supersede** the hours previously in canon (Mon/Tue/Thu 15–20 · Wed 9–20 · Fri 15–21:30 · Sat 9–22:30 · Sun 9–20, from MASTER_PROMPT_THILAND.md §6). Every day now closes earlier except Friday, which extends to 22:00. Wednesday is the only split shift.

### Entry price list

- Child CHF 10 · accompanying adult CHF 3 — both marked "dato confermato" in the model.
- Planning assumption: 1 paying adult per child (modifiable). Average revenue per family unit CHF 13.
- This **resolves the open question** in `10-canon/offer.md` and **contradicts** the marketing plan v1.4 changelog of 5 August ("CHF 10 a persona"), which is what the landing, the plan documents and Google Business Profile currently state. Alex ruled on 24 August that the Business Plan prevails (dec-tl-014).

### Birthday packages — definitive naming and pricing

| Package | Price | Children | Contents |
|---|---|---|---|
| THI PARTY | CHF 18/child | min 10, max 15 | entry + table + games + popcorn + crisps + drink |
| THI PARTY PLUS | CHF 23/child | min 10, max 18 | THI PARTY + pizza |
| THI EXCLUSIVE PARTY | CHF 499 flat | up to 20 | PLUS + exclusive use max 3h + socks + mascot at the cake |
| EXCLUSIVE extra | CHF 18/child | 21st to 25th | surcharge beyond 20 children |

This closes two blockers that WP-04 carried as 🔴: the naming conflict (contract said Bronze/Platino/Gold, the document used Base/Base con torta/Completo — **both are now dead**) and the definitive pricing. Anti-slip socks are included in **all three** packages by Alex's decision of 24 August (dec-tl-015); the model only spells them out for EXCLUSIVE.

Volume assumptions and margins (prudent / central / positive): 4/6/8 PARTY per month · 2/4/6 PLUS · 1/2/3 EXCLUSIVE. Annual birthday revenue CHF 21,252 / 44,088 / 72,252 against variable costs of CHF 5,664 / 12,096 / 20,352 — contribution margin around **72–73%** in all three. Variable cost assumptions: CHF 4 per child PARTY, CHF 8 per child PLUS, CHF 120 base EXCLUSIVE.

### Memberships

THI **STANDARD** CHF 49/month · THI PLUS CHF 69/month · THI FAMILY CHF 99/month · THI **FOUNDER CHF 350 one-off**.

Two things change against canon: the entry tier is named **STANDARD**, not START; and Founder is explicitly **una tantum**, which resolves the "annual recurring vs one-off until age 10" question flagged as urgent in the overview. Founder volumes modelled at 30/60/90 for year one (CHF 10,500 / 21,000 / 31,500), kept out of recurring revenue and treated as year-one cash.

Recurring membership revenue is modelled only in the prudent column (15 STANDARD + 5 PLUS + 3 FAMILY = CHF 16,524/year); central and positive are +5% and +10% of that figure rather than separate volume assumptions.

### Cost base and break-even

- Staff: two employees at 80% of a CHF 4,500 gross monthly salary, plus 17 h/week of hourly support at CHF 25/h. Total **CHF 124,755/year** including 15% employer charges.
- Rent CHF 4,500/month (CHF 54,000/year); other operating costs CHF 3,000/month (CHF 36,000/year, "stima prudenziale"). Initial equipment investment CHF 50,000, flagged as an input still to confirm.
- **Break-even is 45.4 children per day** on entries alone, against a prudent scenario of 30 and a central scenario of 50.

### Scenarios and result

| Scenario | Children/day | Recurring revenue | Recurring EBITDA | Year-1 cash |
|---|---|---|---|---|
| Prudent | 30 | CHF 179,627 | **−40,793** | −80,293 |
| Central | 50 | CHF 297,856 | +71,005 | +42,005 |
| Positive | 75 | CHF 445,055 | +209,948 | +191,448 |

## Direct implications

- **The prudent scenario loses money.** At 30 children/day the park is roughly 15 below break-even and burns CHF 80k in year one once the equipment investment is counted. The gap between prudent and viable is about 15 children a day — which is precisely what marketing has to deliver. This reframes the ADV budget question (`ev-tl-003`, task `ev-tl-003-t3`): CHF 3,000 over seven months to move a business whose survival hinges on ~15 incremental children per day is a number worth re-examining rather than simply confirming.
- Birthdays carry a ~72% contribution margin — the highest-margin line in the model and, per WP-04, also the main acquisition engine. They deserve more weight in the marketing plan than they currently have.
- Every published surface stating "CHF 10 a persona" is now wrong: landing `thiland.ch`, the WP documents, Google Business Profile. Adults pay CHF 3.
- The membership tier renamed STANDARD invalidates the four digital card designs delivered in Phase 1 if they carry the word START (Allegato A lists START/PLUS/FAMILY/FOUNDER). To verify against the produced artwork.
- Canon hours in `10-canon/offer.md` are superseded; `10-canon/operations.md` needs the staffing pattern, which is operational knowledge it does not yet hold.
- Socks: the model prices entry at CHF 10 with socks sold separately at CHF 5 and mandatory to play, but assigns no revenue line to them. With socks included in all birthday packages (dec-tl-015) at CHF 1 unit cost, the effect on package margin is about CHF 1 per child — immaterial against the 72% margin.

## Candidate tasks

Filed to NXTO as `ev-tl-004-t1` … `ev-tl-004-t4`.

1. Verify the Phase 1 digital card artwork: does it say START or STANDARD?
2. Re-examine the ADV budget against a break-even gap of ~15 children/day, rather than simply reconfirming CHF 3,000.
3. Confirm the CHF 50,000 initial equipment investment, still marked as an input to confirm.
4. Define the maximum number of parties per day and the bookable slots — still open in WP-04 and now needed for the booking flow.

## Candidate decisions

Recorded as dec-tl-014 … dec-tl-018 in `30-decisions/decision-log.md`.

## Candidate canon

Amendments to `10-canon/offer.md` (price list, birthday packages, memberships, hours, break-even) and `10-canon/operations.md` (opening hours with staffing coverage). Both files are `status: accepted`, so they are amended with an explicit `supersedes` link on a `canon/` branch awaiting Alex's merge.
