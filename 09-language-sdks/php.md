# PHP SDK

## What It Is
The **PHP OTel SDK** (`opentelemetry-php`) provides API/SDK plus auto-instrumentation via an extension/agent for PHP apps (Laravel, Symfony).

## Why It Exists
PHP web apps need request-level tracing and metrics with minimal code changes.

## Key Components
| Component | Use |
|-----------|-----|
| `opentelemetry-php` (API/SDK) | Core |
| `opentelemetry-php-instrumentation` | Auto-instr extension |
| `opentelemetry-exporter-otlp` | OTLP |

## Code Example
```php
use OpenTelemetry\SDK\Trace\TracerProvider;
$tracer = $tracerProvider->getTracer('example');
$span = $tracer->spanBuilder('do_work')->startSpan();
$span->end();
```

## Best Practices
- Use the auto-instrumentation extension for breadth
- Export OTLP to a Collector
- Set `OTEL_SERVICE_NAME` via env

## Caveats
- Some features less mature than Go/Java
- Check stability before relying on metrics

## Related Concepts
- [Auto / Zero-Code](../08-instrumentation/auto-zero-code.md)
- [Stability Matrix](stability-matrix.md)
