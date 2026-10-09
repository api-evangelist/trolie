---
generated: '2026-10-09'
method: generated
name: submit-forecast-rating-proposal
description: As a Ratings Provider, submit a forecast rating proposal to a TROLIE Clearinghouse Provider, check its status, then read back the forecast limits snapshot in use.
api: openapi/trolie-openapi.yml
operations: [patchRatingForecastProposal, getRatingForecastProposalStatus, getLimitsForecastSnapshot]
source: Grounded in openapi/trolie-openapi.yml (TROLIE 1.1.0, from https://trolie.energy/openapi-1.0.yaml); every operationId verified verbatim in that spec.
---
# Submit a forecast rating proposal

1. Get an OAuth 2.0 client-credentials token (scheme `oauth2-primary-flow`) with `write:forecast-proposals`, `read:forecast-proposals` and `read:operating-snapshot`.
2. `patchRatingForecastProposal` — `PATCH /rating-proposals/forecast` with `Content-Type: application/vnd.trolie.rating-forecast-proposal.v1+json` (or the slim variant `application/vnd.trolie.rating-forecast-proposal-slim.v1+json; limit-type=apparent-power`). Expect `202 Accepted`.
3. `getRatingForecastProposalStatus` — `GET /rating-proposals/forecast` to see whether proposals are complete and which were invalid or late. Send `If-None-Match` with the last `ETag`; `304` means nothing changed.
4. `getLimitsForecastSnapshot` — `GET /limits/forecast-snapshot` to read the limits the Transmission Provider is using. You can narrow it with `offset-period-start`, `period-end`, `resource-id-filter`, `static-only` and `temporal-resolution`.

Rules: `409` means a conflicting proposal, `413` means the payload is too large, `415` means the media type is wrong and `422` means a semantic validation failure. `400`, `406`, `409`, `410`, `415` and `422` return RFC 9457 problem details; `401`, `403`, `404`, `413`, `429` and `500` have empty bodies. On `429`, honour `Retry-After`. Nothing in the spec defines an idempotency key, but resubmitting the full proposal through PATCH replaces it, so a retry is safe.
