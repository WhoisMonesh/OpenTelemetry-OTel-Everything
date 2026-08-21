# Python SDK

## What It Is
The **Python OTel SDK** (`opentelemetry-python`) provides API/SDK plus easy **auto-instrumentation** via the `opentelemetry-instrument` wrapper.

## Why It Exists
Python services (web, data, ML) benefit from low-friction instrumentation, including zero-code coverage.

## Key Packages
| Package | Use |
|---------|-----|
| `opentelemetry-api` | API |
| `opentelemetry-sdk` | SDK |
| `opentelemetry-exporter-otlp-proto-grpc` | OTLP exporter |
| `opentelemetry-instrumentation-*` | Libraries + auto-instr |

## Code Example (auto)
```bash
pip install opentelemetry-distro opentelemetry-exporter-otlp
opentelemetry-bootstrap -a install
opentelemetry-instrument python app.py
```

## Code Example (manual)
```python
from opentelemetry import trace
tracer = trace.get_tracer(__name__)
with tracer.start_as_current_span("work") as s:
    s.set_attribute("key", "value")
```

## Best Practices
- Use `opentelemetry-instrument` for breadth
- Set `OTEL_SERVICE_NAME`, `OTEL_EXPORTER_OTLP_ENDPOINT`
- Use `LoggingHandler` to bridge logs

## Related Concepts
- [Auto / Zero-Code](../08-instrumentation/auto-zero-code.md)
- [Libraries](../08-instrumentation/libraries.md)
