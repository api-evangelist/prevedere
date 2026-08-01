---
name: Read a Board Foresight forecast model and its projection
description: List forecast models, retrieve a model's forecast, and pull its statistics and risk analysis from the Board Foresight (Prevedere) API.
api: openapi/prevedere-openapi-original.json
operations:
  - GET /forecastmodels
  - GET /forecastmodel/{ForecastModelId}
  - GET /forecast/{ForecastModelId}
  - GET /forecast/statistics/{ForecastModelId}
  - GET /forecast/risk/{ForecastModelId}
---

# Read a Board Foresight forecast

Use this skill to pull an economic forecast from the Board Foresight (formerly Prevedere) API.

## Authentication
All requests take an API key in the `ApiKey` query parameter, e.g. `?ApiKey=YOUR_KEY`. Base URL: `https://api.prevedere.com`.

## Steps
1. **List available models** — `GET /forecastmodels` to enumerate forecast models. List endpoints support `Page` and `PageSize` query parameters.
2. **Inspect a model** — `GET /forecastmodel/{ForecastModelId}` for the model definition and metadata.
3. **Get the forecast** — `GET /forecast/{ForecastModelId}` to retrieve the projected series.
4. **Assess quality** — `GET /forecast/statistics/{ForecastModelId}` for accuracy statistics and `GET /forecast/risk/{ForecastModelId}` for risk bands.

## Conventions & errors
- Rate limited: every operation can return `429 Too Many Requests`; back off and retry.
- `404 Not Found` means the `ForecastModelId` does not exist; `403` means the key lacks access to that company context.
- `410 Gone` marks retired endpoints — migrate to the current path.
- Responses are `application/json` (not RFC 9457 problem+json). See `conventions/prevedere-conventions.yml`.
