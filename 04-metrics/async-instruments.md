# Async Instruments

## What It Is
**Asynchronous instruments** (observables) report values via a **callback** when the SDK collects, rather than being recorded inline by application code.

## Why It Exists
Some measurements (CPU, memory, external system state) can only be sampled on demand, not recorded at event time. Async instruments fit this model.

## Async Instrument Types
| Instrument | Monotonic | Example |
|------------|-----------|---------|
| `ObservableCounter` | yes | bytes read from disk |
| `ObservableUpDownCounter` | no | active connections |
| `ObservableGauge` | n/a | temperature, CPU % |

## Architecture
```mermaid
graph LR
    SDK[SDK collects] --> CB[Invoke callback]
    CB --> V[Report value(s)]
```

## When to Use It
- System/runtime metrics
- Values you can't increment at event time
- Reporting a snapshot of external state

## Code Example (Python)
```python
def report_cpu(_observer):
    _observer.observe(cpu_percent(), {"cpu": "total"})
meter.register_observable_gauge("system.cpu.utilization", report_cpu)
```

## Best Practices
- Keep callbacks fast (they run on collection interval)
- Avoid blocking I/O in callbacks
- Don't mix sync recording and async for the same logical metric

## Related Concepts
- [Gauge](gauge.md)
- [Counter](counter.md)
- [Metric Streams](metric-streams.md)
