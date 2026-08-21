# Index Lifecycle Management (ILM)

## What It Is
**ILM** automates the **lifecycle** of Elasticsearch indices/data streams: rollover, then transition through hot→warm→cold→delete tiers.

## Why It Exists
Logs grow forever; ILM keeps hot data fast/expensive only while needed, then moves it to cheaper tiers and deletes it on schedule.

## Phases
```mermaid
graph LR
    H[Hot: SSD, write] --> W[Warm: HDD] --> C[Cold: object] --> D[Delete]
```

## Example Policy
```json
{
  "policy": {
    "phases": {
      "hot":  { "actions": { "rollover": { "max_size": "50gb", "max_age": "1d" } } },
      "warm": { "min_age": "7d",  "actions": { "shrink": {...} } },
      "cold": { "min_age": "30d", "actions": { "searchable_snapshot": {} } },
      "delete": { "min_age": "90d", "actions": { "delete": {} } }
    }
  }
}
```

## When to Use It
- Always for log data streams
- Per-criticality retention (audit longer)

## Best Practices
- Attach ILM to index templates / data streams
- Tune rollover sizes to shard size
- Monitor ILM execution (Stack Monitoring)

## Related Concepts
- [Data Streams](data-streams.md)
- [Retention (essentials)](../18-logging-essentials/retention.md)
- [Indexing (essentials)](../18-logging-essentials/indexing.md)
