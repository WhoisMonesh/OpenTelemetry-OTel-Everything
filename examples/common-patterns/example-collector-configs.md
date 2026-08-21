# Example Collector Configurations

Reusable Collector config snippets for common scenarios.

## A. Host metrics + OTLP → Prometheus + Tempo
```yaml
receivers:
  otlp: { protocols: { grpc: {}, http: {} } }
  hostmetrics:
    collection_interval: 30s
    scrapers: { cpu: {}, memory: {}, disk: {}, network: {} }
processors:
  memory_limiter: { check_interval: 1s, limit_mib: 2000 }
  batch: {}
  k8sattributes: {}
exporters:
  prometheus: { endpoint: 0.0.0.0:8889 }
  otlp/tempo: { endpoint: tempo:4317, tls: { insecure: true } }
service:
  pipelines:
    traces:  { receivers: [otlp], processors: [memory_limiter, batch, k8sattributes], exporters: [otlp/tempo] }
    metrics: { receivers: [otlp, hostmetrics], processors: [memory_limiter, batch, k8sattributes], exporters: [prometheus] }
```

## B. SpanMetrics connector (RED from traces)
```yaml
connectors:
  spanmetrics:
    histogram: { explicit: { buckets: [0.05,0.1,0.25,0.5,1,2.5,5,10] } }
exporters:
  prometheus: { endpoint: 0.0.0.0:8889 }
service:
  pipelines:
    traces:  { receivers: [otlp], processors: [batch], exporters: [spanmetrics] }
    metrics: { receivers: [spanmetrics], exporters: [prometheus] }
```

## C. Redact secrets
```yaml
processors:
  attributes/redact:
    actions:
      - { key: "authorization", action: delete }
      - { key: "enduser.id", action: delete }
```

See [Collector Config Cheatsheet](../../cheat-sheets/collector-config.md) and [Processors](../../02-architecture/processors.md).
