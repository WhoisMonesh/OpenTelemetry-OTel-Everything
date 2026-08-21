# Structured Logging

## What It Is
**Structured logging** emits logs as **machine-readable key-value records** (typically JSON/NDJSON) instead of free-form text lines.

## Why It Exists
Plain-text logs are hard to query at scale ("find all 5xx for user X in the last hour"). Structured logs turn every log into queryable fields.

## Structured vs Unstructured
| | Unstructured | Structured |
|--|--------------|------------|
| Form | `"ERROR order 42 failed: timeout"` | `{"level":"error","order_id":42,"error":"timeout"}` |
| Query | regex/grep only | field filters (`level:error AND order_id:42`) |
| Cost | high (full-text) | lower (field-indexed) |

## Example (JSON)
```json
{"timestamp":"2026-08-21T10:00:00Z","level":"error","service":"checkout","order_id":42,"error":"timeout"}
```

## When to Use It
- Always in production / microservices
- Paired with Kibana/Coralogix field queries

## Best Practices
- Emit JSON/NDJSON from the app (or bridge via OTel)
- Use consistent field names (see ECS / semconv)
- Keep the message + structured fields both
- Redact secrets before emitting

## Related Concepts
- [Log Formats](log-formats.md)
- [ECS (Kibana)](../19-kibana-elastic/ecs.md)
- [Enrichment](enrichment.md)
