---
id: ev-tl-003
client_id: thi-land
record_type: evidence
service_path: company
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: "chat://cowork-session/2026-08-20-21-open-questions"
schema_version: 1.1.0
created_at: 2026-08-21
updated_at: 2026-08-21
---
# Evidence — Alex resolves the brain's open questions (chat session)

- Source: working session with Alex Bellesia in Cowork, 20–21 August 2026. Fourteen open questions accumulated across `ev-tl-001`, `ev-tl-002`, `10-canon/brand.md` and the manifest were put to the authority and answered directly.
- Actors: Alex Bellesia (authority, Spatial Port Inc.). No client-side input in this session — several answers are explicitly marked as pending Daniele Pronzini's confirmation.
- Redaction result: nothing removed. No secrets, no personal data beyond the named business contacts already in canon.

## Factual summary — answers given

**Brand and sub-brand**

1. **THI RESTAURANT scope** — inside contract SP-2026-THI-001, **logo only**. Any further restaurant work makes it a client in its own right with ad-hoc invoicing. This bounds the sub-brand engagement precisely: the brandbook section and the two logo variants are the deliverable, nothing more.
2. **Restaurant legal entity** — a **separate entity** from KRISTAL SA. Details not yet known; a placeholder stands until confirmed.
3. **Mascot and the restaurant** — the mascot is **deliberately excluded** from THI RESTAURANT. The omission in the brandbook section was intentional, and is now stated.
4. **70/30 red-to-green ratio** — a **binding rule**, verifiable at review, not a guideline. It is the defence against the Italian-tricolour read.
5. **Public mascot name** — **THI**. OKKIO remains the name of the management software only. This closes the naming conflict open since `ev-tl-001`.
6. **Arton font licence** — **purchased by the client**, consistent with art. 9.2 (premium font licences excluded from the contract, client-payable). Covers the lettering reused for the second commercial mark.
7. **Legal name in the manifest** — KRISTAL SA is the paying entity and must **never appear in public-facing material**; THI LAND is the public name. `legal_name` in the manifest is internal metadata and can carry the legal entity, provided the public-name rule is written next to it.

**Preview operations (24–25 October 2026)**

8. **Accompanying adults** — **free** at the preview. Marked as Alex's working assumption, **to be confirmed with Daniele**. This is consistent with the published «famiglia 2+2 = CHF 28 invece di 60» claim and with «300 posti = 300 bambini».
9. **Per-shift cap** — 30 **children** per shift, not 30 people. Ten shifts × 30 = 300 children. With accompanying adults in the room, real occupancy reaches roughly 60–80 people per shift, against a documented ~100-person space capacity.
10. **Anti-slip socks unit cost** — **CHF 1.00** per pair. Against a CHF 7 ticket, after Stripe fees of roughly CHF 0.50, net contribution is about **CHF 5.50 per ticket**, so about **CHF 1.650 net on 300 tickets** — versus CHF 2.100 gross. The offer is sound; the margin is not eroded as feared.

**Contracts and delivery**

11. **Software IP conflict** — **OKKIO art. 12 prevails** over the main contract art. 7: the client holds a perpetual, irrevocable, non-exclusive licence for up to 10 sites; the source code does not transfer. This reverses the manifest's current `software_owner: client` and the client-specific exception stated in `CLAUDE.md`. See Direct implications — this is the most consequential answer in the session.
12. **ADV budget of record** — **to be reconfirmed with Daniele**. The CHF 3.000 / ~7 months figure from marketing plan v1.4 versus roughly EUR 1.200/month from contract-era material remains unresolved. ROAS of ~0.62 depends on which one holds.
13. **Phase 1 print deliverables** — uniforms, exterior totem/signage and the 4×3 billboard with QR are **all approved and in production**. Phase 1 is genuinely closed.
14. **DE/EN tone of voice** — **not done; Italian only for now**. Landing, social and Google Business Profile are IT-only. The contract foresees IT + DE + EN for public material, so this is a known, accepted gap rather than an oversight.
15. **OKKIO Phase 1 MVP vs the 15 September 2026 deadline** — **status unknown**, Alex to verify. Fewer than four weeks remain and the points/access system is expected to be operating by the 31 October opening.

## Direct implications

- `10-canon/brand.md` — five of its "Open questions" are now answered (mascot name, Arton licence, Phase 1 print production, DE/EN adaptation) and the mascot section's naming conflict resolves to THI. The file is `status: accepted`, so it is amended here with an explicit `supersedes` link rather than edited silently.
- `00-manifest/client-manifest.md` — `software_owner: client` no longer matches the decision on art. 12 and should become `spatial-port`. The client-specific exception described in `CLAUDE.md` ("THI-LAND owns the custom software built for it") is contradicted by this answer and needs the same correction. **Proposed, not applied unilaterally**: it reverses a documented contractual exception and deserves Alex's explicit merge.
- Restaurant `ip_owner` and invoicing cannot be settled until the separate entity is identified. Until then the logo work stays inside SP-2026-THI-001 and is not invoiced separately.
- The preview economics are now fully known: CHF 7 gross, ~CHF 1.50 of cost, ~CHF 5.50 net per child. Usable for the post-31-October pricing decision.
- The per-shift figure of 30 children implies 60–80 people in a ~100-capacity room. Not a violation, but the margin is thinner than the headline number suggests and depends on how many adults accompany each child.

## Candidate tasks

Filed to NXTO as `ev-tl-003-t1` … `ev-tl-003-t5`, not as repository Markdown.

1. Confirm with Daniele that accompanying adults enter free at the 24–25 October preview.
2. Verify the status of OKKIO Phase 1 MVP against the 15 September 2026 deadline.
3. Reconfirm the ADV budget of record with Daniele (CHF 3.000 total vs ~EUR 1.200/month).
4. Identify the legal entity operating THI RESTAURANT and replace the manifest placeholder.
5. Plan the DE/EN tone-of-voice adaptation for public material after the 31 October opening.

## Candidate decisions

Recorded in `30-decisions/decision-log.md` in the same branch.

## Candidate canon

Amendments to `10-canon/brand.md` (mascot name, Arton licence, Phase 1 status, DE/EN gap, sub-brand scope and mascot exclusion) and to `00-manifest/client-manifest.md` (`software_owner`). Proposed on a `canon/` branch so they wait for Alex's merge rather than auto-merging.
