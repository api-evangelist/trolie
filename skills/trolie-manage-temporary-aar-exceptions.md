---
generated: '2026-10-09'
method: generated
name: manage-temporary-aar-exceptions
description: Create, list, read, update and delete temporary Ambient Adjusted Rating (AAR) exceptions in TROLIE.
api: openapi/trolie-openapi.yml
operations: [createTemporaryAARException, getTemporaryAARExceptions, getTemporaryAARException, updateTemporaryAARException, deleteTemporaryAARException]
source: Grounded in openapi/trolie-openapi.yml (TROLIE 1.1.0, from https://trolie.energy/openapi-1.0.yaml); every operationId verified verbatim in that spec.
---
# Manage temporary AAR exceptions

1. Token scopes needed: `write:temporary-aar-exceptions` and `read:temporary-aar-exceptions`.
2. `createTemporaryAARException` — `POST /temporary-aar-exceptions` with `application/vnd.trolie.temporary-aar-exception.v1+json`. Expect `201`.
3. `getTemporaryAARExceptions` — `GET /temporary-aar-exceptions`. Filter with `period-start`, `period-end` and `segment-filter`.
4. `getTemporaryAARException` — `GET /temporary-aar-exceptions/{id}`.
5. `updateTemporaryAARException` — `PUT /temporary-aar-exceptions/{id}`. Expect `204`.
6. `deleteTemporaryAARException` — `DELETE /temporary-aar-exceptions/{id}`. Expect `204`.
