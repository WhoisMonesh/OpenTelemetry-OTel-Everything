# Go SDK

## What It Is
The **Go OTel SDK** (`go.opentelemetry.io/otel`) provides traces, metrics, and logs for Go applications.

## Why It Exists
Go services (esp. microservices/infra) need first-class, performant instrumentation with context propagated via `context.Context`.

## Key Packages
| Package | Use |
|---------|-----|
| `go.opentelemetry.io/otel` | API (Tracer/Meter) |
| `go.opentelemetry.io/otel/sdk` | SDK |
| `go.opentelemetry.io/otel/exporters/otlp/*` | OTLP exporters |
| `go.opentelemetry.io/contrib/instrumentation/*` | Library instrumentation |

## Code Example
```go
tp := otel.NewTracerProvider(
    otel.WithBatcher(otlptracegrpc.NewClient().(otlptrace.Client)),
)
otel.SetTracerProvider(tp)
tracer := otel.Tracer("example")
ctx, span := tracer.Start(ctx, "doWork")
defer span.End()
```

## Best Practices
- Pass `context.Context` everywhere (Go uses it for span context)
- Use contrib instrumentation for `net/http`, `grpc`, `database/sql`
- Batch via `WithBatcher`

## Caveats
- No full zero-code agent; use contrib or eBPF
- Metrics API is stable; configure MeterProvider

## Related Concepts
- [Manual Instrumentation](../08-instrumentation/manual.md)
- [eBPF](../08-instrumentation/ebpf.md)
