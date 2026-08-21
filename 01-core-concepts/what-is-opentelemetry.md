# What Is OpenTelemetry?

## What It Is
OpenTelemetry (OTel) is a **vendor-neutral, open-source observability framework** for generating, collecting, and exporting **telemetry** (traces, metrics, logs, and profiles) from software systems.

## Why It Exists
Before OTel, every observability backend shipped its own SDK. Switching vendors meant rewriting instrumentation. OTel provides:
- A **single standard API/SDK** for all signals
- A **standard wire protocol (OTLP)**
- **Pluggable exporters** so backends are interchangeable
- **Shared semantic conventions** so data is comparable

It was formed in 2019 by merging **OpenTracing** (tracing API) and **OpenCensus** (metrics + tracing, from Google), and is now a **CNCF graduated project**.

## Architecture
```mermaid
graph LR
    A[App Code] --> B[OTel API]
    B --> C[OTel SDK]
    C --> D[Exporter]
    D --> E[OTLP]
    E --> F[Collector / Backend]
```

## Key Features
- Vendor-neutral, CNCF graduated
- Supports 3 stable signals + profiling
- Manual + automatic instrumentation
- Works across 11+ languages
- Collector decouples apps from backends

## When to Use It
- You want to avoid observability vendor lock-in
- You need consistent telemetry across polyglot services
- You want to standardize tracing/metrics/logs in one pipeline

## Code Example
```bash
# Install theCollector
docker run -p 4317:4317 -p 4318:4318 otel/opentelemetry-collector:latest

# Send a trace via OTLP/gRPC from an instrumented app
OTEL_EXPORTER_OTLP_ENDPOINT=http://localhost:4317 \
OTEL_SERVICE_NAME=my-app \
./my-app
```

## Best Practices
- Standardize on OTLP end-to-end (avoid proprietary agents where possible)
- Use semantic conventions for attributes
- Deploy a Collector as a buffer between apps and backends

## Common Issues & Solutions
| Issue | Fix |
|-------|-----|
| Too many exporters in app | Move to Collector-side exporters |
| Inconsistent attribute names | Adopt semantic conventions |
| High overhead | Use sampling + Collector batching |

## Interview Questions
**Q: OpenTracing vs OpenCensus vs OpenTelemetry?**
A: OpenTracing provided a tracing API; OpenCensus provided metrics + tracing (Google). They merged into OpenTelemetry, which also added logs and a Collector.

## Related Concepts
- [Signals](signals.md)
- [OTLP](otlp.md)
- [API vs SDK](api-vs-sdk.md)
