# Receiver / Exporter Matrix

Common Collector components at a glance.

## Receivers (in)
| Receiver | Purpose |
|----------|---------|
| `otlp` | Primary OTLP ingest (gRPC/HTTP) |
| `prometheus` | Scrape Prometheus metrics |
| `hostmetrics` | Host CPU/mem/disk |
| `filelog` | Tail log files |
| `jaeger` / `zipkin` | Legacy trace formats |
| `fluentforward` | Fluentd logs |

## Exporters (out)
| Exporter | Destination |
|----------|-------------|
| `otlp` | Collector / OTLP backend |
| `debug` / `logging` | stdout (dev) |
| `prometheus` | Prometheus scrape endpoint |
| `loki` | Logs |
| `otlp/jaeger`, `otlp/tempo` | Traces |
| Vendor | Datadog, New Relic, Honeycomb, Splunk, Elastic |

## Processors (transform)
- `memory_limiter` (first!), `batch`, `resource`, `attributes`, `filter`
- `tail_sampling`, `k8sattributes`, `transform` (OTTL)

## Connectors
- `spanmetrics`, `servicegraph`, `routing`, `count`

See [Collector Pipeline](../02-architecture/collector-pipeline.md) and [Distributions](../06-collector/distributions.md).
