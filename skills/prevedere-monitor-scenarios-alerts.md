---
name: Monitor scenarios and alerts
description: List scenarios, read alert definitions, and pull triggered alerts from the Board Foresight (Prevedere) API to monitor forecast conditions.
api: openapi/prevedere-openapi-original.json
operations:
  - GET /scenarios
  - GET /scenario/{scenarioId}
  - GET /alertdefinitions
  - GET /alerts
---

# Monitor scenarios and alerts

Track scenario outcomes and forecast-driven alerts.

## Authentication
API key in the `ApiKey` query parameter. Base URL: `https://api.prevedere.com`.

## Steps
1. **List scenarios** — `GET /scenarios`, then `GET /scenario/{scenarioId}` for a specific scenario's definition and results.
2. **Read alert definitions** — `GET /alertdefinitions` to see configured alert rules (and `GET /{id}` under AlertDefinition for one).
3. **Pull triggered alerts** — `GET /alerts` to retrieve alert history; filter/paginate with `Page` / `PageSize` where supported.

## Conventions & errors
- `429` = rate limited; back off and retry.
- `404` = scenario or alert id not found; `403` = key lacks access to the company context.
- Responses are `application/json`. See `conventions/prevedere-conventions.yml`.
