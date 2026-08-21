# 01 · Core Concepts

> The foundational building blocks of OpenTelemetry: what it is, the signals it produces, and the core primitives (API, SDK, Resource, Attributes, OTLP, Instrumentation, Exporter) that make up every OTel deployment.

## Topics in this section

| Document | Summary |
|----------|---------|
| [what-is-opentelemetry.md](what-is-opentelemetry.md) | Definition, history, CNCF, scope |
| [observability.md](observability.md) | Observability vs monitoring, the three (now four) pillars |
| [signals.md](signals.md) | Traces, Metrics, Logs, Profiles |
| [otlp.md](otlp.md) | OpenTelemetry Protocol wire format |
| [telemetry-data-model.md](telemetry-data-model.md) | Common data model shared by signals |
| [api-vs-sdk.md](api-vs-sdk.md) | API (interface) vs SDK (implementation) |
| [resource.md](resource.md) | Resource: entity producing telemetry |
| [attributes.md](attributes.md) | Key-value metadata on telemetry |
| [instrumentation.md](instrumentation.md) | How code is instrumented |
| [auto-instrumentation.md](auto-instrumentation.md) | Zero-code instrumentation |
| [exporter.md](exporter.md) | Sending telemetry to a backend |
| [semantic-conventions.md](semantic-conventions.md) | Standard attribute names |
| [context.md](context.md) | Context propagation primitive |
| [stability-levels.md](stability-levels.md) | Stable / experimental stability |

## Quick mental model

```
API  (what you call)  ──►  SDK  (records & batches)  ──►  OTLP  ──►  Collector  ──►  Backend
                              ▲
                       Instrumentation (manual or auto)
                              ▲
                       Resource + Attributes + Context
```

See the [main README](../README.md) for the full map.
