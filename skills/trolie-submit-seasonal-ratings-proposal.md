---
generated: '2026-10-09'
method: generated
name: submit-seasonal-ratings-proposal
description: Submit a seasonal ratings proposal, check its status, and read the seasonal ratings snapshot in use.
api: openapi/trolie-openapi.yml
operations: [patchSeasonalRatingsProposal, getSeasonalRatingProposalStatus, getSeasonalRatingsSnapshot]
source: Grounded in openapi/trolie-openapi.yml (TROLIE 1.1.0, from https://trolie.energy/openapi-1.0.yaml); every operationId verified verbatim in that spec.
---
# Submit a seasonal ratings proposal

1. Token scopes needed: `write:seasonal-proposals`, `read:seasonal-proposals` and `read:operating-snapshot`.
2. `patchSeasonalRatingsProposal` — `PATCH /rating-proposals/seasonal` with `application/vnd.trolie.seasonal-ratings-proposal.v1+json` (or the slim variant). Expect `202`.
3. `getSeasonalRatingProposalStatus` — `GET /rating-proposals/seasonal`.
4. `getSeasonalRatingsSnapshot` — `GET /seasonal-ratings/snapshot`.
