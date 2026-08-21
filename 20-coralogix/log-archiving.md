# Log Archiving (Coralogix)

## What It Is
Coralogix **archives** raw logs to cost-effective object storage (e.g., S3) so you retain everything cheaply and **rehydrate** on demand for investigation.

## Why It Exists
You often must keep logs for compliance (months/years) but rarely query old ones. Archival keeps cost low while preserving data.

## Flow
```mermaid
graph TD
    Logs --> Idx[Indexed (hot, queryable)]
    Logs --> Arc[(S3 archive: cheap)]
    Arc --> Re[Rehydrate → query on demand]
```

## When to Use It
- Compliance / long retention
- Cost control (avoid indexing everything)

## Best Practices
- Archive all logs; index only what you alert on (TCO)
- Encrypt archives at rest
- Document rehydration workflow for incidents

## Related Concepts
- [TCO Optimizer](tco-optimizer.md)
- [Retention (essentials)](../18-logging-essentials/retention.md)
- [Logging Cost](../18-logging-essentials/log-cost.md)
