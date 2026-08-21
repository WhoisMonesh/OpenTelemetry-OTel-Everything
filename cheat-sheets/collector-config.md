# Collector Config Cheatsheet

Minimal and common Collector YAML patterns.

## Minimal (debug)
```yaml
receivers: { otlp: { protocols: { grpc: {}, http: {} } } }
processors:
  memory_limiter: { check_interval: 1s, limit_mib: 2000 }
  batch: {}
exporters: { debug: { verbosity: detailed } }
service:
  pipelines:
    traces:  { receivers: [otlp], processors: [memory_limiter, batch], exporters: [debug] }
    metrics: { receivers: [otlp], processors: [memory_limiter, batch], exporters: [debug] }
    logs:    { receivers: [otlp], processors: [memory_limiter, batch], exporters: [debug] }
```

## Agent (light) → Gateway
```yaml
exporters:
  otlp/gateway: { endpoint: otel-gateway:4317, tls: { insecure: false } }
processors:
  memory_limiter: { check_interval: 1s, limit_mib: 1000 }
  batch: {}
  k8sattributes: {}
```

## Gateway (tail sampling)
```yaml
processors:
  tail_sampling:
    policies:
      - { name: errors, type: status_code, status_code: { status_codes: [ERROR] } }
      - { name: prob, type: probabilistic, probabilistic: { sampling_percentage: 10 } }
```

## Validate
```bash
otelcol --config=collector.yaml validate
```

See [Collector Config](../06-collector/config.md) and [Processors](../02-architecture/processors.md).
