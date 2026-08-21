# OTLP Specification (Overview)

A practical overview of the **OpenTelemetry Protocol (OTLP)**.

## What It Is
OTLP is the **standard wire protocol** for transmitting telemetry between OTel components. It defines Protobuf message schemas and two transports.

## Transports
| Transport | Port | Serialization |
|-----------|------|---------------|
| OTLP/gRPC | `4317` | Protobuf |
| OTLP/HTTP | `4318` | Protobuf (or JSON over HTTP) |

## Services
- `TraceService` → `ExportTraceServiceRequest`
- `MetricsService` → `ExportMetricsServiceRequest`
- `LogsService` → `ExportLogsServiceRequest`
- `ProfilesService` (emerging) → `ExportProfilesServiceRequest`

## Message Shape
Each export request carries:
- `resource_metrics` / `resource_spans` / `resource_logs`
- Each resource → scope (instrumentation library) → data points

## Why gRPC vs HTTP
- **gRPC (4317)**: efficient, multiplexed — preferred inside clusters
- **HTTP (4318)**: easier through proxies/firewalls — preferred at edges

## Best Practices
- Prefer Protobuf (JSON only where required)
- Secure with TLS/mTLS
- Use OTLP end-to-end; avoid bespoke exporters

See [OTLP (core)](../01-core-concepts/otlp.md) and [Exporters](../02-architecture/exporters.md).
