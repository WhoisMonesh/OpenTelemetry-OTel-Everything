# Java SDK

## What It Is
The **Java OTel SDK** provides both a programmatic API and a powerful **zero-code Java agent** (`opentelemetry-javaagent.jar`).

## Why It Exists
Java's JVM enables bytecode instrumentation, giving the best auto-instrumentation coverage of any language.

## Key Components
| Component | Use |
|-----------|-----|
| `opentelemetry-javaagent.jar` | Zero-code agent |
| `opentelemetry-sdk` | Programmatic SDK |
| `opentelemetry-spring-boot-starter` | Spring autoconfig |
| Instrumentation modules | Per-framework coverage |

## Code Example (agent)
```bash
java -javaagent:opentelemetry-javaagent.jar \
     -Dotel.service.name=checkout \
     -Dotel.exporter.otlp.endpoint=http://collector:4317 \
     -jar app.jar
```

## Best Practices
- Prefer the agent for breadth
- Pin agent version; upgrade deliberately
- Avoid mixing agent with another APM agent

## Caveats
- Agent adds startup overhead
- Some frameworks need explicit instrumentation modules

## Related Concepts
- [Auto / Zero-Code](../08-instrumentation/auto-zero-code.md)
- [Kubernetes Deployment](../13-kubernetes-deployment/README.md)
