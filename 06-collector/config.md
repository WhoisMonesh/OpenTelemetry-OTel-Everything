# Collector Config

## What It Is
The Collector is configured via a single **YAML file** defining `receivers`, `processors`, `exporters`, `connectors`, `extensions`, and `service.pipelines`.

## Why It Exists
Declarative config lets operators define pipelines without code and validate them before deploy.

## Structure
```yaml
receivers:
  otlp: { protocols: { grpc: {}, http: {} } }

processors:
  memory_limiter: { check_interval: 1s, limit_mib: 2000 }
  batch: {}

exporters:
  debug: {}

extensions:
  health_check: { endpoint: 0.0.0.0:13133 }

service:
  extensions: [health_check]
  pipelines:
    traces:
      receivers: [otlp]
      processors: [memory_limiter, batch]
      exporters: [debug]
```

## Key Sections
| Section | Purpose |
|---------|---------|
| `receivers` | Data entry points |
| `processors` | Transform/filter |
| `exporters` | Data exits |
| `connectors` | Signal conversion |
| `extensions` | Aux (health, auth) |
| `service.pipelines` | Wires it together |

## When to Use It
- Every Collector deployment
- Use env var substitution (`${env:VAR}`) for secrets

## Best Practices
- Validate with `otelcol --config=... validate`
- Keep `memory_limiter` first in every pipeline
- Reference components before use (typos fail startup)

## Common Issues & Solutions
| Issue | Fix |
|-------|-----|
| "pipeline references unknown component" | Check spelling in `service` |
| OOM | Add/raise `memory_limiter` |

## Related Concepts
- [Pipeline](../02-architecture/collector-pipeline.md)
- [Processors Deep](processors-deep.md)
