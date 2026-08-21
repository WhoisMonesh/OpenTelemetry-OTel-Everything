# Observability

## What It Is
**Observability** is the ability to understand a system's internal state by examining its **external outputs** — without shipping new code. OpenTelemetry is the instrumentation layer that powers observability.

## Why It Exists
Traditional **monitoring** asks "is the system up?" Observability asks "why is it slow for this user?" You cannot predict every failure mode, so you need rich, high-cardinality telemetry to answer novel questions.

## Key Features
- **Three classic pillars**: Traces, Metrics, Logs
- **A fourth emerging pillar**: Continuous Profiling
- High-cardinality, structured data
- Correlation across signals via context

## When to Use It
- Debugging complex distributed systems
- SRE-style reliability engineering
- Incident response and root-cause analysis

## Best Practices
- Correlate traces ↔ metrics ↔ logs via `trace_id`
- Design telemetry for unknown-unknowns (high cardinality)
- Use OpenTelemetry to produce all signals uniformly

## Related Concepts
- [Signals](signals.md)
- [Context Propagation](../07-context-propagation/README.md)
