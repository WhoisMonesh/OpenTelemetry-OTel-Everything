# HTTP Semantic Conventions

## What It Is
Standard attributes for **HTTP client/server spans**: method, route, status, URL components.

## Why It Exists
HTTP is the most common operation; consistent attributes enable standard dashboards/alerts.

## Key Attributes
| Attribute | Example | Notes |
|-----------|---------|-------|
| `http.request.method` | `"GET"` | (was `http.method`) |
| `http.route` | `"/users/{id}"` | Use route, not full URL |
| `http.response.status_code` | `200` | |
| `url.full` | `"https://x/y"` | Avoid high-card URLs |
| `client.address` / `server.address` | `"api"` | |
| `network.protocol.version` | `"1.1"` | |

## Architecture
```mermaid
graph TD
    S[Span GET /users] --> M[http.request.method=GET]
    S --> R[http.route=/users/{id}]
    S --> C[http.response.status_code=200]
```

## When to Use It
- Every HTTP server/client span
- Prefer `http.route` over `url.full` (cardinality)

## Best Practices
- Record `http.route` (templated), not raw URL
- Mark 5xx as ERROR status
- Use constants from semconv libraries

## Related Concepts
- [Attributes (core)](../01-core-concepts/attributes.md)
- [Span Status](../03-traces/span-status.md)
