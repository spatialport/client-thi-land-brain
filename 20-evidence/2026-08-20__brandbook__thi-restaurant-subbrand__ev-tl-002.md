---
id: ev-tl-002
client_id: thi-land
record_type: evidence
service_path: branding
status: proposed
owner: alex-bellesia
authority: alex-bellesia
ip_owner: client
access_scope: internal
sensitivity: confidential
source_ref: "file:///Users/alexbellesia/Documents/Claude/Projects/NXTO/clienti/THI-LAND/THI-RESTAURANT-SUBBRAND.html"
schema_version: 1.1.0
created_at: 2026-08-20
updated_at: 2026-08-20
---
# Evidence — THI RESTAURANT sub-brand brandbook section

- Source: brandbook section authored by Spatial Port Inc., dated 13 August 2026, delivered as a standalone HTML page `clienti/THI-LAND/THI-RESTAURANT-SUBBRAND.html` (41.9 KB), plus the two supplied logo files `THI-RESTAURANT-LOGO-SX.svg` and `THI-RESTAURANT-LOGO-DX.svg` (both `fill="currentColor"`, recolourable via CSS without duplicating the file).
- Actors: Alex Bellesia (author/authority, Spatial Port Inc.); client-side approver not yet recorded. Logo artwork supplied by the client to Spatial Port.
- Redaction result: nothing removed. The document contains no secrets, no personal data and no other client's information — it is design specification only.

## Factual summary

THI RESTAURANT is a sub-brand of THI LAND: the family's restaurant, in the same building (Centro Opti, Via Mesolcina 17, 6533 Lumino TI). It addresses a different moment of the day — the table, not the play.

**Brand architecture.** The two brands are deliberately given *independent colour worlds*. The only declared link is the shared type system: the same «THI» lettering root and Outfit as the text face on both. Governing rule: the «THI» lettering is never redrawn for either brand.

**Logo.** A two-line lockup — «THI» smaller above, «RESTAURANT» extended below defining the width. Two variants exist, differing only in which side «THI» aligns to; internal proportions never change. SX is the default. Variant choice is typographic, not aesthetic: «THI» aligns to the edge that governs the layout.

| Context | Variant |
|---|---|
| Letterhead, site header, menu, left-ranged signage | SX |
| Footer, right column, closing signature, bottom-right corner | DX |
| Next to the THI LAND logo | DX if THI RESTAURANT sits left, SX if right |
| Centred (packaging, stickers, napkins) | SX |

Never mix the two variants in the same piece.

**Clear space and minimum sizes.** Clear space equals the height of the «THI» block on all four sides. Minimum widths: digital 140 px · print 35 mm (45 mm on rough paper or fabric) · embroidery and screen print 50 mm.

**Chromatic versions.** The logo is monochromatic by construction: Rosso Brace on light grounds, Panna on dark or saturated grounds. Four approved versions: positive (Brace on panna), negative (Panna on espresso), on Rosso Brace, on Verde Oliva. Ocra and Verde Oliva are system colours, not logo colours.

**Palette (dedicated, not derived from THI LAND) — WCAG 2.1 verified.**

| Role | Name | Hex | Contrast |
|---|---|---|---|
| Primary | Rosso Brace | `#B3402F` | 5.1:1 on panna · AA |
| Secondary | Verde Oliva | `#5E6B3B` | 5.1:1 on panna · AA |
| Light accent | Ocra Dorata | `#E0A22E` | 7.0:1 on espresso · AAA |
| Text accent | Senape Scura | `#8F6110` | 4.8:1 on panna · AA |
| Light neutral | Panna | `#F7F1E6` | main ground |
| Mid neutral | Sabbia | `#E8DCC8` | surfaces and panels |
| Dark neutral | Espresso | `#2B211C` | 14.0:1 on panna · AAA |

Rationale: wood-oven red, fresh-herb green, crust and oil ochre, on a dough-and-tablecloth cream ground. Red leads, green accompanies, indicatively **70/30** — equal parts produce an unavoidable Italian-tricolour read that trivialises the mark. Ocra must never be set as text on panna (2.0:1, illegible). Espresso must not be substituted with pure black in print.

**Coexistence with THI LAND.** Because the palettes are independent, shared materials require neutral ground: pure white or neutral grey, never panna nor mint (each is a brand's home field). Both logos in espresso `#2B211C` or both in white, same optical size — never one in colour and the other not. No brand accents at all on shared materials: brace red and fluo lime vibrate unpleasantly side by side. Hierarchy follows ownership of the piece. What declares the family is the «THI» lettering and Outfit — nothing else needs forcing.

**Typography.** No new typefaces. Outfit SemiBold/Bold for titles, Outfit Regular for text; the logo lockup is drawn lettering (Arton, customised) used only via the supplied files, never recomposed from a font.

## Direct implications

- THI LAND canon `10-canon/brand.md` currently documents a single brand. It now needs a sub-brand layer: THI RESTAURANT exists, has its own palette, and the brand system link is typographic only. Proposed as candidate canon in the same branch.
- The forbidden-use list is a constraint on every future generated asset for this client: teal, lime and orange must never colour the THI RESTAURANT mark, and no brand accent may appear on any THI LAND × THI RESTAURANT shared material.
- Delivery surface changed: the THI LAND client portal (`projects/thi-land/presentazioni/index.html`) gained card 1.2 "THI RESTAURANT" linking to a dedicated page, and `deploy-aws/deploy.sh` now copies `thi-restaurant-subbrand.html` plus both logo SVGs to the portal bucket.
- The section lives as a standalone HTML file, not inside `NXTO/THI-LAND-BRAND-BOOK.html`. The brandbook of record is therefore currently split across two files.
- Open question in `10-canon/brand.md` about the Arton licence now carries more weight: the lettering is reused for a second commercial mark.

## Candidate tasks

Filed as proposals to NXTO (`ev-tl-002-t1` … `ev-tl-002-t4`), not as repository Markdown.

1. Verify that the Arton font licence covers derivative lettering reused for a second commercial mark (THI RESTAURANT), and who holds it.
2. Merge the THI RESTAURANT section into the master brandbook `THI-LAND-BRAND-BOOK.html` so there is one brandbook of record.
3. Obtain written client approval of the THI RESTAURANT palette and of the coexistence rules before any applied artwork is produced.
4. Apply the sub-brand to the first real touchpoints (menu, insegna, tovagliette, packaging) and validate the minimum sizes against the actual production processes.

## Candidate decisions

- Is THI RESTAURANT inside the scope of contract SP-2026-THI-001, or does it require a separate quote? The signed contract's Allegato A does not list restaurant brand work.
- Confirm the operating entity behind the restaurant (KRISTAL SA, as for THI LAND, or a separate entity) — it determines `ip_owner` and invoicing for this service path.
- Confirm that the mascot does not extend to the restaurant. The section makes no mention of OKKIO/THI; the omission looks deliberate but is not stated.
- Confirm the 70/30 red-to-green ratio as a binding rule rather than a guideline, since it is the main defence against the tricolour read.

## Candidate canon

Proposed additions to `10-canon/brand.md` in the same branch, `status: proposed` — a "Sub-brand: THI RESTAURANT" block covering architecture, logo variants and selection rule, clear space and minimum sizes, chromatic versions, palette with contrast ratios, forbidden uses, coexistence rules and typography. Promotion to accepted is Alex's call.
