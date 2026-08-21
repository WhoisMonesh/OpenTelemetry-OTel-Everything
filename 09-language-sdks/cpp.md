# C++ SDK

## What It Is
The **C++ OTel SDK** (`opentelemetry-cpp`) provides tracing and metrics for native C/C++ applications.

## Why It Exists
Native services (game engines, HFT, embedded, legacy) need OTel without a managed runtime.

## Key Components
| Component | Use |
|-----------|-----|
| `opentelemetry-cpp` (API) | API |
| `opentelemetry-cpp` (SDK) | SDK |
| `otlp exporter` | OTLP/gRPC or HTTP |
| `opentelemetry-cpp-contrib` | Additional exporters |

## Code Example
```cpp
auto provider = std::make_shared<trace::TracerProvider>();
auto tracer = provider->GetTracer("example");
auto span = tracer->StartSpan("do_work");
// ... work ...
span->End();
```

## Best Practices
- Build with CMake; link API + SDK
- Use the OTLP exporter to a Collector
- Prefer eBPF for truly uninstrumentable binaries

## Caveats
- Build complexity higher than managed langs
- Smaller instrumentation library ecosystem

## Related Concepts
- [eBPF](../08-instrumentation/ebpf.md)
- [Manual Instrumentation](../08-instrumentation/manual.md)
