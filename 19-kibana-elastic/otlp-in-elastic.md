# Ingesting OpenTelemetry in Elastic

## What It Is
Elasticsearch/Kibana can **natively ingest OpenTelemetry** via the Elastic exporter (OTLP) — logs, metrics, and traces land in Elastic without a separate OTel Collector (or via one).

## Why It Exists
Teams using OTel SDKs can send directly to Elastic, mapping OTLP → ECS automatically, avoiding vendor lock-in at the SDK layer.

## Two Paths
```mermaid
graph TD
    A[OTel SDK] --> OTLP[OTLP] --> EA[Elastic Agent (OTel)]
    EA --> ES[(Elasticsearch)]
    A --> C[OTel Collector] --> E[Elastic exporter] --> ES
```

## How
- **Elastic Agent** running in OTel collector mode, or
- **OTel Collector** with the `elasticsearchexporter` (or Elastic exporter), mapping to ECS data streams (`logs-*`, `metrics-*`, `traces-*`).

## Env Example
```bash
OTEL_EXPORTER_OTLP_ENDPOINT=https://<your-deployment>:443
OTEL_EXPORTER_OTLP_HEADERS="Authorization=Bearer <token>"
```

## Best Practices
- Let Elastic map OTLP → ECS (no manual field surgery)
- Use the `traces` data stream for APM correlation
- Correlate OTel `trace.id` with logs in Discover

## Related Concepts
- [ECS](ecs.md)
- [Data Streams](data-streams.md)
- [OTel Exporters (core)](../10-exporters-backends/elastic.md)
