# JavaScript / TypeScript SDK

## What It Is
The **JS/TS OTel SDK** (`@opentelemetry/*`) covers Node.js backends and browser frontends.

## Why It Exists
Full-stack JS needs both server-side (Express, Nest, GraphQL) and client-side (fetch, Web Vitals) instrumentation, linked by trace context.

## Key Packages
| Package | Use |
|---------|-----|
| `@opentelemetry/sdk-node` | Node SDK |
| `@opentelemetry/api` | API |
| `@opentelemetry/instrumentation-*` | Express, pg, grpc, etc. |
| `@opentelemetry/sdk-trace-web` | Browser |
| `@opentelemetry/exporter-trace-otlp-http` | OTLP/HTTP |

## Code Example (Node)
```js
const { NodeTracerProvider } = require('@opentelemetry/sdk-node');
const { OTLPTraceExporter } = require('@opentelemetry/exporter-trace-otlp-grpc');
const provider = new NodeTracerProvider();
provider.addSpanProcessor(new BatchSpanProcessor(new OTLPTraceExporter()));
provider.register();
```

## Best Practices
- Use `registerInstrumentations` for auto coverage
- Export via OTLP/HTTP from browsers
- Propagate `traceparent` on `fetch`/XHR

## Related Concepts
- [Web Instrumentation](../08-instrumentation/web.md)
- [Auto / Zero-Code](../08-instrumentation/auto-zero-code.md)
