# Manual Instrumentation

## What It Is
**Manual instrumentation** means explicitly calling the OTel API in your code to create spans, record metrics, and emit logs.

## Why It Exists
Auto-instrumentation covers frameworks, but **business logic** (a checkout flow, a calculation) needs manual spans to be observable.

## When to Use It
- Critical business operations
- Custom workflows not covered by libraries
- Adding domain-specific attributes

## Code Example (Python)
```python
from opentelemetry import trace
tracer = trace.get_tracer("shop")
with tracer.start_as_current_span("checkout") as span:
    span.set_attribute("order.total", total)
    span.set_attribute("user.tier", tier)
    process_payment()
```

## Best Practices
- Wrap meaningful operations, not every line
- Add semantic attributes
- Combine with auto-instrumentation for breadth

## Related Concepts
- [Auto / Zero-Code](auto-zero-code.md)
- [API vs SDK](../01-core-concepts/api-vs-sdk.md)
- [Language SDKs](../09-language-sdks/README.md)
