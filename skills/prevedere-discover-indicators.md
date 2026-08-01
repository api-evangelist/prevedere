---
name: Discover leading economic indicators and correlations
description: Search economic indicators, retrieve their time series, and run correlation discovery against a business metric using the Board Foresight (Prevedere) API.
api: openapi/prevedere-openapi-original.json
operations:
  - GET /search
  - GET /indicator/{Provider}/{ProviderId}
  - GET /indicator/series/{Provider}/{ProviderId}
  - GET /correlation/{FixedProvider}/{FixedProviderId}/{LeadingProvider}/{LeadingProviderId}/{Frequency}/{Calculation}
---

# Discover leading indicators and correlations

Find external economic signals that lead a business metric.

## Authentication
API key in the `ApiKey` query parameter. Base URL: `https://api.prevedere.com`.

## Steps
1. **Search indicators** — `GET /search` with a `Query` term to find economic indicators; paginate with `Page` / `PageSize`.
2. **Read an indicator** — `GET /indicator/{Provider}/{ProviderId}` for metadata and `GET /indicator/series/{Provider}/{ProviderId}` for its time series values.
3. **Correlate** — `GET /correlation/{FixedProvider}/{FixedProviderId}/{LeadingProvider}/{LeadingProviderId}/{Frequency}/{Calculation}` to measure how a leading indicator correlates with a fixed series at a given frequency and calculation.

## Conventions & errors
- `429` signals rate limiting; retry with backoff.
- `404` means the `Provider`/`ProviderId` pair is unknown; `422` means the request parameters failed validation.
- Responses are `application/json`. See `conventions/prevedere-conventions.yml` and `errors/prevedere-problem-types.yml`.
