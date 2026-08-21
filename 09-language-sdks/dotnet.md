# .NET SDK

## What It Is
The **OpenTelemetry .NET SDK** (`OpenTelemetry.*`) provides tracing, metrics, and logs for .NET / ASP.NET Core apps, with strong auto-instrumentation.

## Why It Exists
.NET services (enterprise, cloud) need first-class, well-integrated observability with minimal code.

## Key Packages
| Package | Use |
|---------|-----|
| `OpenTelemetry` | API/SDK core |
| `OpenTelemetry.Extensions.Hosting` | ASP.NET Core integration |
| `OpenTelemetry.Instrumentation.AspNetCore` | HTTP server |
| `OpenTelemetry.Exporter.OpenTelemetryProtocol` | OTLP |

## Code Example
```csharp
builder.Services.AddOpenTelemetry()
    .WithTracing(t => t
        .AddSource("my-app")
        .AddAspNetCoreInstrumentation()
        .AddOtlpExporter());
```

## Best Practices
- Use the hosting extensions for ASP.NET Core
- Auto-instrumentation available via `OpenTelemetry.AutoInstrumentation`
- Export OTLP to a Collector

## Related Concepts
- [Auto / Zero-Code](../08-instrumentation/auto-zero-code.md)
- [Libraries](../08-instrumentation/libraries.md)
