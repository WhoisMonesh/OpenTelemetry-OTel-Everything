# Ruby SDK

## What It Is
The **Ruby OTel SDK** (`opentelemetry-ruby`) provides API/SDK plus gems for Rails, Sinatra, and common libraries, with auto-instrumentation.

## Why It Exists
Ruby/Rails apps need low-friction observability integrated with the framework.

## Key Gems
| Gem | Use |
|-----|-----|
| `opentelemetry-sdk` | SDK |
| `opentelemetry-exporter-otlp` | OTLP |
| `opentelemetry-instrumentation-rails` | Rails |
| `opentelemetry-instrumentation-*` | Other libs |

## Code Example
```ruby
require 'opentelemetry/sdk'
require 'opentelemetry/exporter/otlp'
OpenTelemetry::SDK.configure do |c|
  c.service_name = 'checkout'
  c.use_all   # enable all available instrumentation
end
```

## Best Practices
- Use `use_all` for breadth (dev), explicit in prod
- Export OTLP to Collector
- Bridge Rails logs with the log correlation

## Related Concepts
- [Libraries](../08-instrumentation/libraries.md)
- [Auto / Zero-Code](../08-instrumentation/auto-zero-code.md)
