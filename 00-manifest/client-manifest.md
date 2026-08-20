---
client_id: thi-land
legal_name: "THI-LAND"
brain_spec_version: 1.1.0
authority: alex-bellesia
account_owner: alex-bellesia
active_service_paths: [branding, content, crm, landing-pages, local-seo, paid-media, software]
client_window_enabled: false
client_window_policy: accepted-client-scope-only
software_owner: client
deliverable_owner: client
source_file_owner: client
client_data_owner: client
videogo_enabled: false
drive_root_ref: gdrive://shared-drive-thi-land-TBD
dashboard_client_ref: dashboard://thi-land
credential_collection_ref: password-manager://spatial-port/thi-land
machine_secret_prefix: aws-secretsmanager://spatial-port/prod/thi-land/
retention_policy: contract-plus-legal-hold
created_at: 2026-08-11
updated_at: 2026-08-19
---
# Client Manifest

Complete every field. Unknown is allowed only as an explicit value such as `tbd`, never as a missing field.

## Contract exception

THI-LAND owns the custom software created under its signed exception. Confirm the exact source-code, infrastructure and derivative-work clauses before enabling software delivery.

Note (2026-08-19, unverified nuance from sources): the main services contract SP-2026-THI-001 (art. 7) transfers full IP including source code to the client upon full payment, while the OKKIO software contract SP-2026-THI-OKKOI/OKKIO-001 (art. 12, THI-LAND-OKKIO-CONTRATTO.md) grants a perpetual, irrevocable, non-exclusive licence for up to 10 sites rather than an ownership transfer; client data remains client-owned with guaranteed export. Reconcile these clauses with the signed exception before software handover. Keep `software_owner: client` as agreed until Alex rules otherwise.

## Change notes

- 2026-08-19 — Workspace audit (ev-tl-001): bumped brain_spec_version to 1.1.0; populated active_service_paths from contract/deliverable evidence (branding, content, crm, landing-pages, local-seo, paid-media, software); confirmed client legal entity in sources is KRISTAL SA (UID CHE-115.363.630), represented by Daniele Pronzini — `legal_name` left as "THI-LAND" pending Alex review. Canon files 10-canon/* filled with proposed knowledge from primary sources; see 20-evidence/2026-08-19__workspace-audit__thi-land-sources__ev-tl-001.md.
