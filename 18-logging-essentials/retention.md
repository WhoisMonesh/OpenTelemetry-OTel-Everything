# Retention & Lifecycle

## What It Is
**Retention** defines how long logs are kept and how they're tiered (hot → warm → cold → delete) to balance cost and access.

## Why It Exists
Storing everything forever is expensive; retaining nothing kills forensics. Lifecycle management automates tiering and deletion.

## Tiers (Elasticsearch ILM)
| Tier | Media | Access | Cost |
|------|-------|--------|------|
| Hot | SSD | Frequent | High |
| Warm | HDD | Occasional | Medium |
| Cold | Object store | Rare | Low |
| Delete | — | — | Free |

## Coralogix Approach
Coralogix uses a **metrics-based / TCO-optimized** model — frequent logs become metrics/alerts, raw logs archived cost-effectively (often S3), reducing indexing cost.

## When to Use It
- Define retention per log criticality (audit vs debug)
- Tier hot→cold→delete automatically

## Best Practices
- Short hot retention (days), long cold (months) for compliance
- Sample/archive verbose logs
- Separate retention for security vs app logs

## Related Concepts
- [Indexing](indexing.md)
- [ILM (Kibana)](../19-kibana-elastic/ilm.md)
- [Log Cost](log-cost.md)
- [Coralogix TCO](../20-coralogix/tco-optimizer.md)
