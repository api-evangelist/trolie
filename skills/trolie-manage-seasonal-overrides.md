---
generated: '2026-10-09'
method: generated
name: manage-seasonal-overrides
description: Create, list, read, update and delete temporary seasonal rating overrides in TROLIE.
api: openapi/trolie-openapi.yml
operations: [createSeasonalOverride, getSeasonalOverrides, getSeasonalOverride, updateSeasonalOverride, deleteSeasonalOverride]
source: Grounded in openapi/trolie-openapi.yml (TROLIE 1.1.0, from https://trolie.energy/openapi-1.0.yaml); every operationId verified verbatim in that spec.
---
# Manage seasonal overrides

1. Token scopes needed: `write:seasonal-overrides` and `read:seasonal-overrides`.
2. `createSeasonalOverride` — `POST /seasonal-overrides` with `application/vnd.trolie.seasonal-override.v1+json`. Expect `201`.
3. `getSeasonalOverrides` — `GET /seasonal-overrides`. Filter with `period-start`, `period-end` and `segment-filter`.
4. `getSeasonalOverride` — `GET /seasonal-overrides/{id}`. `410` means the override is gone.
5. `updateSeasonalOverride` — `PUT /seasonal-overrides/{id}`. Expect `204`.
6. `deleteSeasonalOverride` — `DELETE /seasonal-overrides/{id}`. Expect `204`; `409` means a conflict.
