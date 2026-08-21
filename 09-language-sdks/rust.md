# Rust SDK

## What It Is
The **Rust OTel SDK** (`opentelemetry-rust`) provides tracing and metrics for Rust services, with async-friendly, zero-cost design.

## Why It Exists
Rust services (high-performance infra, edge) need OTel support without sacrificing performance or safety.

## Key Crates
| Crate | Use |
|-------|-----|
| `opentelemetry` | API |
| `opentelemetry-sdk` | SDK |
| `opentelemetry-otlp` | OTLP exporter |
| `tracing-opentelemetry` | Bridge `tracing` → OTel |
| `opentelemetry-stackdriver`/others | Vendor exporters |

## Code Example
```rust
use opentelemetry::trace::Tracer;
let tracer = opentelemetry::global::tracer("example");
let span = tracer.start("do_work");
// ... work ...
span.end();
```

## Best Practices
- Bridge the popular `tracing` crate via `tracing-opentelemetry`
- Use `tokio`/`async` exporters
- Batch spans with the `BatchSpanProcessor`

## Caveats
- Metrics API evolving; check stability
- Some exporters community-maintained

## Related Concepts
- [Manual Instrumentation](../08-instrumentation/manual.md)
- [Stability Matrix](stability-matrix.md)
