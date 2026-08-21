# Log Query Languages

## What It Is
The languages you use to **search and analyze** logs across platforms: **KQL** and **Lucene** (Kibana/Elastic), and **DataPrime** (Coralogix), plus SQL-like options.

## Why It Exists
Different platforms expose different query syntaxes; knowing them lets you find logs fast.

## Comparisons
| Platform | Language | Example |
|----------|----------|---------|
| Kibana/Elastic | **KQL** | `service.name: checkout and log.level: error` |
| Kibana/Elastic | **Lucene** | `service.name:checkout AND level:error` |
| Coralogix | **Lucene-style / DataPrime** | `application:checkout AND level:error` |

## KQL Tips
- Field:value (no operator for AND-ish)
- `field: value1 or value2`
- Range: `response.status_code >= 500`
- Nested: `error.message: timeout`

## Coralogix DataPrime
Step-by-step pipeline: filter → group by → aggregate (like a logs SQL).

## Best Practices
- Learn KQL for Elastic, DataPrime for Coralogix
- Save frequent queries as views/dashboards
- Use `trace.id` to pivot to traces

## Related Concepts
- [Discover (Kibana)](../19-kibana-elastic/discover.md)
- [Query & Dataflow (Coralogix)](../20-coralogix/query-dataflow.md)
- [Troubleshooting with Logs](troubleshooting-with-logs.md)
