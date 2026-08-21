# Diagnostic Runbooks

## What It Is
An **end-to-end diagnostic flow** for OpenTelemetry issues, from symptom to fix.

## Why It Exists
When telemetry breaks, you need a fast, repeatable path to root cause rather than guessing.

## The Flow
```mermaid
graph TD
    S[Symptom] --> L1[Is data leaving the app? debug exporter]
    L1 --> L2[Is the Collector receiving? health_check/metrics]
    L2 --> L3[Is the Collector exporting? send_failed_*]
    L3 --> L4[Is the backend receiving? backend UI]
    L4 --> R[Root cause + fix]
```

## Quick Commands
```bash
# Confirm Collector health
curl http://collector:13133/healthz

# Confirm internal metrics
curl http://collector:8888/metrics | grep dropped

# Local debug export from app
OTEL_EXPORTER_OTLP_ENDPOINT=... OTEL_TRACES_EXPORTER=debug python app.py
```

## Best Practices
- Start at the source, move outward
- Use `debug` exporter to isolate tiers
- Monitor the Collector's own metrics proactively

## Related Concepts
- [Missing Spans](missing-spans.md)
- [Dropped Data](dropped-data.md)
- [Collector Errors](collector-errors.md)
