# Interview Cheatsheet

## Quick Recall
| Topic | Key fact |
|-------|----------|
| Signals | Traces, Metrics, Logs, Profiles |
| OTLP ports | gRPC `4317`, HTTP `4318` |
| Collector order | `memory_limiter` first, then `batch` |
| Agent | DaemonSet, per node, light |
| Gateway | Deployment, central, tail sampling |
| Span tree | root has no parent; children nest |
| Propagation | W3C `traceparent` + `tracestate` |
| Baggage | custom KV that propagates |
| Sampling | head (SDK) / tail (gateway) |
| Exemplars | metric → trace link |
| RED | Rate, Errors, Duration |
| USE | Utilization, Saturation, Errors |
| Connector | signal→signal (spanmetrics) |
| Resource | `service.name` required-ish |

## Minimal Collector Config
```yaml
receivers: { otlp: { protocols: { grpc: {}, http: {} } } }
processors: { memory_limiter: { check_interval: 1s, limit_mib: 2000 }, batch: {} }
exporters: { debug: {} }
service:
  pipelines:
    traces: { receivers: [otlp], processors: [memory_limiter, batch], exporters: [debug] }
```

## Env Vars
```
OTEL_SERVICE_NAME=checkout
OTEL_EXPORTER_OTLP_ENDPOINT=http://collector:4317
OTEL_EXPORTER_OTLP_PROTOCOL=grpc
OTEL_TRACES_SAMPLER=parentbased_always_on
```

## Related Concepts
- [Questions](questions.md)
- [Concepts](concepts.md)
