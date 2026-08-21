# Tutorial: Local Quickstart

Send traces from a tiny app through the Collector to debug/Jaeger locally.

## 1. Start the Collector (debug)
`collector.yaml`:
```yaml
receivers: { otlp: { protocols: { grpc: {}, http: {} } } }
processors: { memory_limiter: { check_interval: 1s, limit_mib: 1000 }, batch: {} }
exporters: { debug: { verbosity: detailed } }
service:
  pipelines:
    traces: { receivers: [otlp], processors: [memory_limiter, batch], exporters: [debug] }
```
```bash
otelcol --config=collector.yaml
```

## 2. Instrument a Python app
```bash
pip install opentelemetry-distro opentelemetry-exporter-otlp
opentelemetry-bootstrap -a install
```
```python
from opentelemetry import trace
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import BatchSpanProcessor
from opentelemetry.exporter.otlp.proto.grpc.trace_exporter import OTLPSpanExporter

trace.set_tracer_provider(TracerProvider())
trace.get_tracer_provider().add_span_processor(
    BatchSpanProcessor(OTLPSpanExporter(endpoint="http://localhost:4317")))
tracer = trace.get_tracer("quickstart")

with tracer.start_as_current_span("hello") as s:
    s.set_attribute("example", "yes")
    print("span emitted")
```

## 3. Run
```bash
OTEL_SERVICE_NAME=quickstart OTEL_EXPORTER_OTLP_ENDPOINT=http://localhost:4317 \
OTEL_EXPORTER_OTLP_PROTOCOL=grpc python app.py
```
Watch the Collector stdout print the span.

## Next
Point the exporter at **Jaeger/Tempo** instead of `debug` — see [Jaeger](../../10-exporters-backends/jaeger.md).

See also [Instrumentation](../../08-instrumentation/README.md).
