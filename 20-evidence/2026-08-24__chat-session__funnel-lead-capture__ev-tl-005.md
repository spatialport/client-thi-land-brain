---
id: ev-tl-005
client_id: thi-land
record_type: evidence
service_path: landing-pages
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: "chat://cowork-session/2026-08-24-funnel-lead-capture"
schema_version: 1.1.0
created_at: 2026-08-24
updated_at: 2026-08-24
---
# Evidence — The preview funnel changes from direct sale to invitation

- Source: working session with Alex Bellesia in Cowork, 24 August 2026.
- Actors: Alex Bellesia (authority). No client-side input recorded for this change.
- Redaction result: nothing removed.

## Factual summary

The preview funnel is split in two. `thiland.ch` stops selling and starts collecting email addresses; the sale moves to a separate page reachable only from the invitation email.

**New structure**

| Page | Purpose | Indexed | Fires |
|---|---|---|---|
| `thiland.ch/` (`landing-invito.html`) | Collect email addresses for the invitation | Yes | `generate_lead` |
| `thiland.ch/biglietto.html` | Stripe checkout at CHF 7 | No — `noindex` + `Disallow` | `begin_checkout` |
| `thiland.ch/grazie.html` | Post-payment | No — `Disallow` | `purchase` |

The lead form posts to the existing waitlist backend (API Gateway `/iscrizione`, DynamoDB dedupe on email, Brevo list 3), with `source: landing-invito-anteprima`. Honeypot field `email_address_check` preserved.

**Copy decisions**

- The number **300 is removed from all public copy**. Scarcity now rests on a closed number without a figure and on the concrete constraint: **turns of 2 hours, maximum 30 children**, framed as a quality guarantee rather than a limitation ("si gioca davvero", no crowding).
- Exclusivity is stated plainly: entry is by invitation, not everyone will get in, the access does not repeat.
- **The CHF 7 price stays visible on the lead landing**, in the section explaining what the invitation unlocks and in the FAQ. It is not the headline. This is deliberate: hiding the price to raise lead volume would make the invitation email feel like a bait-and-switch, and the brand voice explicitly forbids vague promises.
- Guarantee language changed from "rimborso garantito" (meaningless with no purchase) to "nessun impegno, ti scriviamo solo per questo".

**New asset**: `projects/thi-land/email/invito-anteprima.html`, the invitation email carrying the only link to the purchase page.

## Direct implications

- **Google Ads is now optimising for the wrong conversion.** The campaign was built around `begin_checkout` / `purchase` on the landing. The landing no longer fires either. Until a `generate_lead` conversion action is created in GA4, imported into Ads and set as the campaign objective, Smart Bidding is optimising against an event that will never fire. This is the single most urgent consequence of the change.
- The ROAS figures in WP-14 and WP-07 no longer describe the funnel: the landing's conversion is a lead, not a sale. Cost per lead and lead-to-purchase rate become the metrics that matter, and neither has a baseline yet.
- Sale volume now depends on a second step (the email) that did not exist before. The preview revenue of CHF 2,100 is no longer a function of landing traffic alone.
- `deploy-checkout.sh` and the Stripe Lambda now point at `biglietto.html`; `CANCEL_URL` updated to `https://thiland.ch/biglietto.html#acquista`.
- `deploy-waitlist.sh` now injects the form endpoint into `landing-invito.html`.
- Stripe still needs `sk_live` and a CHF 7 price from Daniele before the invitation email can be sent at all — the blocker moved but did not disappear.

## Candidate tasks

Filed to NXTO as `ev-tl-005-t1` … `ev-tl-005-t3`.

1. Create the `generate_lead` conversion in GA4, import it into Google Ads and switch the campaign objective — before spend continues.
2. Rewrite the WP-14 and WP-07 funnel metrics around cost per lead and lead-to-purchase conversion.
3. Set up the invitation email in Brevo on the `landing-invito-anteprima` segment and decide the send date.

## Candidate decisions

Recorded as dec-tl-019 and dec-tl-020 in `30-decisions/decision-log.md`.

## Candidate canon

Amendment to `10-canon/channels.md` describing the two-page funnel, and to `10-canon/offer.md` noting that the preview ticket is sold by invitation only.
