# Env Vars Cheatsheet

Common OpenTelemetry environment variables.

## Core
| Variable | Purpose |
|----------|---------|
| `OTEL_SERVICE_NAME` | Service name (resource) |
| `OTEL_RESOURCE_ATTRIBUTES` | Comma `k=v` resource attrs |
| `OTEL_EXPORTER_OTLP_ENDPOINT` | Collector endpoint |
| `OTEL_EXPORTER_OTLP_PROTOCOL` | `grpc` (4317) or `http/protobuf` (4318) |
| `OTEL_TRACES_EXPORTER` | e.g., `otlp`, `none`, `debug` |
| `OTEL_METRICS_EXPORTER` | e.g., `otlp`, `none` |
| `OTEL_LOGS_EXPORTER` | e.g., `otlp`, `none` |
| `OTEL_TRACES_SAMPLER` | `always_on`, `always_off`, `parentbased_always_on`, `traceidratio` |
| `OTEL_TRACES_SAMPLER_ARG` | ratio (e.g., `0.1`) |
| `OTEL_PROPAGATORS` | `tracecontext,baggage` |

## Example
```bash
export OTEL_SERVICE_NAME=checkout
export OTEL_EXPORTER_OTLP_ENDPOINT=http://localhost:4317
export OTEL_EXPORTER_OTLP_PROTOCOL=grpc
export OTEL_TRACES_SAMPLER=parentbased_always_on
export OTEL_RESOURCE_ATTRIBUTES=deployment.environment=production,service.version=1.2.3
```

See [API vs SDK](../01-core-concepts/api-vs-sdk.md) and [Sampling](../02-architecture/sampling.md).
