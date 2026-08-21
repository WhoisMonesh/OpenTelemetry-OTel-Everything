# Composite Propagators

## What It Is
A **Composite Propagator** chains multiple propagators so a service can **emit and accept several context formats simultaneously** (e.g., W3C + B3).

## Why It Exists
During migration, some downstream services speak W3C and others speak B3. A composite propagator lets one service interoperate with both.

## How It Works
- On **inject**: writes headers for *all* configured propagators
- On **extract**: reads from whichever format is present

## Architecture
```mermaid
graph LR
    A[Service] -->|traceparent + X-B3-*| B[Downstream]
```

## When to Use It
- Mixed environments (Zipkin + OTel)
- Migration periods

## Code Example (Go)
```go
prop := propagation.NewCompositeTextMapPropagator(
    propagation.TraceContext{},
    propagation.Baggage{},
    b3.New(),
)
otel.SetTextMapPropagator(prop)
```

## Best Practices
- Keep W3C first (it's the standard)
- Remove legacy propagators after migration
- Avoid too many (header bloat)

## Related Concepts
- [Propagators](propagators.md)
- [B3](b3.md)
- [Trace Context](trace-context.md)
