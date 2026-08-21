# Glossary

## Terms & Acronyms
| Term | Meaning |
|------|---------|
| **OTel** | OpenTelemetry |
| **OTLP** | OpenTelemetry Protocol |
| **SDK** | Software Development Kit (implementation) |
| **API** | Application Programming Interface (contract) |
| **Span** | A single operation in a trace |
| **Trace** | A tree of spans for one request |
| **Resource** | The entity producing telemetry |
| **Scope** | The instrumentation library/source |
| **Attribute** | Key-value metadata |
| **Exemplar** | Example trace linked to a metric point |
| **Baggage** | Custom KV propagated across services |
| **Propagator** | Injects/extracts context across boundaries |
| **Receiver** | Collector data entry |
| **Processor** | Collector in-flight transform |
| **Exporter** | Collector data exit |
| **Connector** | Signal→signal converter |
| **RED** | Rate, Errors, Duration |
| **USE** | Utilization, Saturation, Errors |
| **SLO** | Service Level Objective |
| **SLI** | Service Level Indicator |
| **eBPF** | Extended Berkeley Packet Filter (kernel) |
| **W3C Trace Context** | Standard `traceparent` propagation |

## Related Concepts
- [Core Concepts](concepts.md)
- [Cheatsheet](cheatsheet.md)
