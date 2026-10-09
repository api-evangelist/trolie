---
generated: '2026-10-09'
method: generated
name: manage-monitoring-sets
description: Create, read, update and delete TROLIE monitoring sets (the power system resources a party exchanges ratings for), and fetch the caller's default set.
api: openapi/trolie-openapi.yml
operations: [createMonitoringSet, getMonitoringSet, updateMonitoringSet, deleteMonitoringSet, getDefaultMonitoringSet]
source: Grounded in openapi/trolie-openapi.yml (TROLIE 1.1.0, from https://trolie.energy/openapi-1.0.yaml); every operationId verified verbatim in that spec.
---
# Manage monitoring sets

1. Token scopes needed: `write:monitoring-sets` and `read:monitoring-sets`.
2. `createMonitoringSet` — `POST /monitoring-sets` with `application/vnd.trolie.monitoring-set-request.v1+json`. Expect `201` with a `Location` header. `409` means the set already exists.
3. `getMonitoringSet` — `GET /monitoring-sets/{id}`. Keep the `ETag`.
4. `updateMonitoringSet` — `PUT /monitoring-sets/{id}` with `application/vnd.trolie.monitoring-set.v1+json`. Expect `204`.
5. `deleteMonitoringSet` — `DELETE /monitoring-sets/{id}`. Expect `204`.
6. `getDefaultMonitoringSet` — `GET /default-monitoring-set`.

Rules: a PUT replaces the whole set. `400`, `406`, `409`, `410`, `415` and `422` return RFC 9457 problem details; the other errors have empty bodies.
