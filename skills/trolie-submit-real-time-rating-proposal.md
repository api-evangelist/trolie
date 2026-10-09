---
generated: '2026-10-09'
method: generated
name: submit-real-time-rating-proposal
description: Submit a real-time (ambient-adjusted) rating proposal, confirm its status, and read the real-time limits snapshot.
api: openapi/trolie-openapi.yml
operations: [postRealTimeProposal, getRealTimeProposalStatus, getRealTimeLimits, getRegionalRealTimeLimits]
source: Grounded in openapi/trolie-openapi.yml (TROLIE 1.1.0, from https://trolie.energy/openapi-1.0.yaml); every operationId verified verbatim in that spec.
---
# Submit a real-time rating proposal

1. Token scopes needed: `write:realtime-proposals`, `read:realtime-proposals` and `read:operating-snapshot`.
2. `postRealTimeProposal` — `POST /rating-proposals/realtime` with `application/vnd.trolie.rating-realtime-proposal.v1+json` (or the slim `...-slim.v1+json; limit-type=apparent-power`). Expect `202`.
3. `getRealTimeProposalStatus` — `GET /rating-proposals/realtime`.
4. `getRealTimeLimits` — `GET /limits/realtime-snapshot`. Use `getRegionalRealTimeLimits` (`GET /limits/regional/realtime-snapshot`) for the regional view. Both accept `resource-id-filter`.

Rules: use conditional GETs (`ETag` / `If-None-Match` → `304`). `400`, `406`, `409`, `410`, `415` and `422` return RFC 9457 problem details; the other errors have empty bodies. On `429`, back off according to `Retry-After`.
