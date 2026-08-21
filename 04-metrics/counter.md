# Counter

## What It Is
A **Counter** is a synchronous instrument that **records increasing values** (e.g., request count, bytes sent). It is **monotonic** by default.

## Why It Exists
Counters are the basis for rates (requests/sec, errors/sec) — the most common SLI.

## Variants
| Instrument | Behavior |
|------------|----------|
| `Counter` | Monotonic sum (only goes up) |
| `UpDownCounter` | Can decrease (e.g., active connections) |

## Architecture
```mermaid
graph LR
    Code[request handler] --> C[Counter.Add(1)]
    C --> Sum[Sum over time]
```

## When to Use It
- Count events: requests, errors, jobs
- UpDownCounter for in-flight / queue depth

## Code Example (Python)
```python
from opentelemetry.metrics import get_meter
meter = get_meter("checkout")
req_counter = meter.create_counter("checkout.requests")
req_counter.add(1, {"http.status_code": "200"})
```

## Best Practices
- Use attributes for dimensions (status, route)
- Keep dimensions low-cardinality
- Use `UpDownCounter` for gauges-like counts

## Related Concepts
- [Gauge](gauge.md)
- [Views](views.md)
- [Metric Streams](metric-streams.md)
