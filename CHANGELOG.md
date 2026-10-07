# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

## 1.0.0 (2026-10-07)

### ⚠ BREAKING CHANGES

- `tombaApiKey` and `tombaApiSecret` inputs were removed. The Actor now uses built-in Tomba credentials from the `TOMBA_API_KEY` / `TOMBA_API_SECRET` environment variables, so users no longer need a Tomba account.

### Features

- Pay-per-event pricing: 2 `tomba-request` events ($0.00312 each, $0.00624 in total) per billable combined lookup, matching Tomba's 2-credit cost; errors, empty results and cache hits are free
- Each item includes `chargedCredits`
- No client-side rate limit; parallel processing with `maxConcurrency`
- Automatic retries with exponential backoff for network errors, 429 and 5xx (`maxRetries`)
- Cross-run result cache (`useCache`, `cacheTtlHours`)
- Resume after migration or restart
- Emails are trimmed, lowercased and deduplicated
- Each dataset item now includes `charged` and `cached`; emails with no result now produce an item with `error` instead of being skipped
- Real-time API (Standby mode): `GET /?email=…` or `POST /` with the run input returns `{ items }` instantly; OpenAPI description in `.actor/web_server_schema.json`
- Key-value store schema (`INPUT`, `TOMBA_STATE`)
- Default memory set to 256 MB

### Dependencies

- `tomba` upgraded to 1.1.1 (responses are now `{ data, rateLimit }`)
- `apify` upgraded to 3.7.2

### 0.0.2 (2025-10-20)
