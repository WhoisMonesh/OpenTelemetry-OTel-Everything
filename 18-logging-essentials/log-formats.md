# Log Formats

## What It Is
Common **on-disk/wire log formats**: plain text, `logfmt`, JSON, and NDJSON (newline-delimited JSON).

## Why It Exists
Format determines how easily logs can be parsed and queried downstream. NDJSON is the sweet spot for centralized logging.

## Formats
| Format | Example | Notes |
|--------|---------|-------|
| Plain | `2026-08-21 ERROR order failed` | Needs parsing |
| logfmt | `level=error order_id=42 error=timeout` | Simple, grep-friendly |
| JSON | `{"level":"error","order_id":42}` | Structured |
| NDJSON | one JSON per line | Streaming-friendly |

## Why NDJSON Wins
```mermaid
graph LR
    A[App] -->|NDJSON line| B[Shipper buffers]
    B -->|batch| C[Backend parses per field]
```
- One object per line → easy streaming/back-pressure
- No multiline ambiguity
- Native for Elasticsearch / Coralogix / Loki

## When to Use It
- Production: NDJSON/JSON
- Avoid multiline stack traces in the message (use structured `exception.stacktrace`)

## Best Practices
- Emit one JSON object per line
- Include `timestamp` (ISO-8601, UTC) and `level`
- Avoid embedding multiline blobs; use fields

## Related Concepts
- [Structured Logging](structured-logging.md)
- [Parsing](parsing.md)
