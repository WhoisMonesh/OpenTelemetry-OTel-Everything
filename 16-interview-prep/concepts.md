# Core Concepts to Know

## What It Is
The set of OpenTelemetry concepts every practitioner should be able to explain.

## Must-Know List
1. **Signals**: Traces, Metrics, Logs, Profiles
2. **OTLP**: the standard wire protocol (gRPC 4317 / HTTP 4318)
3. **API vs SDK**: interface vs implementation
4. **Resource / Attributes / Context**
5. **Collector pipeline**: receivers → processors → exporters (+ connectors, extensions)
6. **Agent vs Gateway** deployment
7. **Sampling**: head (SDK) vs tail (gateway)
8. **Span**: trace tree, parent/child, status, links, events
9. **Context propagation**: W3C `traceparent`, baggage
10. **Semantic Conventions**
11. **Exemplars** (metrics ↔ traces)
12. **RED / USE / Golden Signals**
13. **SLOs** from OTel metrics
14. **Auto-instrumentation** vs manual

## How to Study
- Read the matching section in this repo
- Run the [OpenTelemetry Demo](../14-observability-practice/opentelemetry-demo.md)
- Build a Collector config from scratch

## Related Concepts
- [Questions](questions.md)
- [Learning Path](learning-path.md)
