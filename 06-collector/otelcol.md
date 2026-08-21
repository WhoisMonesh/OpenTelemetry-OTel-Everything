# OpenTelemetry Collector (otelcol)

## What It Is
The **OpenTelemetry Collector** (`otelcol`) is a **vendor-agnostic agent/service** that receives, processes, and exports telemetry. It is the recommended hub of any OTel deployment.

## Why It Exists
Moving collection out of applications decouples them from backends, centralizes processing (sampling, redaction, routing), and reduces per-app overhead and config.

## Key Capabilities
- Receive OTLP + many legacy formats
- Process with 50+ processors
- Export to 50+ backends
- Run as agent, gateway, or sidecar
- Extensible via the builder (`ocb`)

## Architecture
```mermaid
graph LR
    R[Receivers] --> P[Processors] --> E[Exporters]
```

## When to Use It
- Essentially every production OTel setup
- When you want to switch backends without app changes

## Code Example
```bash
otelcol --config=collector.yaml
# or via Docker
docker run -v $(pwd)/collector.yaml:/etc/collector.yaml \
  otel/opentelemetry-collector-contrib:latest
```

## Best Practices
- Always include `memory_limiter` (first) + `batch`
- Use the **contrib** distribution for full component set
- Separate agent and gateway tiers

## Related Concepts
- [Collector Pipeline](../02-architecture/collector-pipeline.md)
- [Distributions](distributions.md)
- [Config](config.md)
