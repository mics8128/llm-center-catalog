# llm-center-catalog

Online model metadata and provider sync defaults for `mics8128/llm-center`.

Raw URL:

```txt
https://raw.githubusercontent.com/mics8128/llm-center-catalog/main/catalog.json
```

`llm-center` can fetch this pack on startup when `APP_CATALOG_AUTO_REFRESH=true` and can refresh manually through:

```txt
POST /api/model-catalog/refresh
```

## Contents

- `provider_sync_defaults`: default include/exclude globs per provider kind.
- `entries`: model metadata keyed by provider kind, upstream model glob, and endpoint type.

Metadata fields use llm-center units:

- token prices: micro-USD per 1M tokens
- TTS text prices: micro-USD per 1M characters
- audio prices: micro-USD per GB when upstream bills audio by time/tokens, converted conservatively for llm-center accounting
- context/output: tokens

## Notes

- Image generation endpoint live-probed on CLIProxy 2026-05-10:
  - `POST /v1/images/generations`, model `gpt-image-2` => 200 OK, JSON with `b64_json`.
- Image edits endpoint returned validation (not 404) in smoke probe, but llm-center does not proxy `/v1/images/edits` yet.
- Pricing/context data should cite official pricing/model docs when possible.
