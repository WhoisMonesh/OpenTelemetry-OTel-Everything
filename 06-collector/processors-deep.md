# Processors — Deep Dive

## What It Is
An advanced look at **processor patterns** for production Collectors: ordering, redaction, tail sampling, k8s enrichment, and transform via OTTL.

## Why It Exists
Real pipelines need more than `batch` — compliance redaction, smart sampling, and metadata enrichment require deliberate processor design.

## Patterns
### 1. Safety-first ordering
```yaml
processors:
  memory_limiter:    # MUST be first
  batch:
```
### 2. Redaction
```yaml
attributes/redact:
  actions:
    - { key: "enduser.id", action: delete }
    - { key: "authorization", action: delete }
```
### 3. K8s enrichment (agent)
```yaml
k8sattributes:
  auth_type: serviceAccount
  pod_association: [{ sources: [{ from: pod }] }]
```
### 4. Transform (OTTL)
```yaml
transform:
  trace_statements:
    - context: span
      statements: ['set(attributes["env"], "prod")']
```

## Architecture
```mermaid
graph LR
    R --> ML[memory_limiter] --> K[k8sattributes] --> T[transform] --> B[batch] --> E
```

## Best Practices
- `memory_limiter` always first
- Use `k8sattributes` on agents, not gateway
- Use OTTL `transform` for complex edits
- Test with `debug` exporter

## Related Concepts
- [Processors (arch)](../02-architecture/processors.md)
- [Connectors](../02-architecture/connectors.md)
- [Security](security.md)
