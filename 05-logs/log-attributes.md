# Log Attributes

## What It Is
**Log attributes** are structured key-value metadata attached to a LogRecord, enabling filtering and correlation beyond the free-text body.

## Why It Exists
A body of "order failed" is unsearchable at scale; attributes (`order.id`, `error.type`) make logs queryable.

## Common Attributes
| Attribute | Example |
|-----------|---------|
| `event.name` | `"order.failed"` |
| `error.type` | `"TimeoutError"` |
| `http.request.method` | `"POST"` |
| `trace_id` / `span_id` | correlation |
| `code.filepath` / `code.lineno` | source location |

## Architecture
```mermaid
graph TD
    L[Log] --> Body[body: "order failed"]
    L --> Attr[attributes: order.id=42]
```

## When to Use It
- Always add structured attributes
- Add `trace_id`/`span_id` for correlation
- Avoid secrets in attributes

## Code Example (Python)
```python
logger.error("order failed", extra={"order.id": 42, "error.type": "TimeoutError"})
```

## Best Practices
- Prefer attributes over parsing the body
- Use semantic conventions for standard keys
- Redact secrets in the Collector `attributes` processor

## Related Concepts
- [Log Record](log-record.md)
- [Semantic Conventions](../11-semantic-conventions/README.md)
- [Attributes (core)](../01-core-concepts/attributes.md)
