# Processors

## What It Is
A **Processor** transforms, filters, batches, or enriches telemetry **in-flight** within a pipeline.

## Why It Exists
Centralized processing lets you apply consistent policies (redaction, sampling, attribute addition) without changing application code.

## Common Processors
| Processor | Purpose |
|-----------|---------|
| `batch` | Group data for efficient export (essential) |
| `memory_limiter` | Prevent OOM (place first) |
| `resource` | Add/modify resource attributes |
| `attributes` | Add/drop/redact span/metric attributes |
| `filter` | Drop spans/metrics/logs by criteria |
| `tail_sampling` | Sample based on full trace (gateway) |
| `probabilistic_sampling` | Sample by percentage |
| `transform` | Edit telemetry with OTTL |
| `k8sattributes` | Add K8s metadata to spans |

## Architecture
```mermaid
graph LR
    R[Receiver] --> ML[memory_limiter]
    ML --> B[batch]
    B --> EX[Exporter]
```

## When to Use It
- Always: `memory_limiter` (first) + `batch`
- Gateway: `tail_sampling`, `k8sattributes`
- Compliance: `attributes` to redact

## Code Example
```yaml
processors:
  memory_limiter:
    check_interval: 1s
    limit_mib: 2000
  batch:
    timeout: 5s
    send_batch_size: 1024
  attributes/redact:
    actions:
      - key: "enduser.id"
        action: delete
```

## Best Practices
- Order matters: `memory_limiter` must be first
- Use OTTL (`transform`) for complex edits
- Test processor configs with the `debug` exporter

## Related Concepts
- [Sampling](sampling.md)
- [Collector Pipeline](collector-pipeline.md)
- [Troubleshooting](../15-troubleshooting/README.md)
