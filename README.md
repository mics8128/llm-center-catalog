# llm-center-catalog

Online model metadata catalog for `mics8128/llm-center`.

Raw URL:

```txt
https://raw.githubusercontent.com/mics8128/llm-center-catalog/main/catalog.json
```

Used by llm-center admin endpoint:

```txt
POST /api/model-catalog/refresh
```

Pack fields are intentionally simple: provider kind, upstream model glob, endpoint type, context/output token limits, and cost columns in micro-USD units used by llm-center.

## Notes

- Image generation endpoint live-probed on CLIProxy 2026-05-10:
  - `POST /v1/images/generations`, model `gpt-image-2` => 200 OK, JSON with `b64_json`.
- Image edits endpoint returned validation (not 404) in smoke probe, but llm-center does not proxy `/v1/images/edits` yet.
