# Log Levels

## What It Is
**Log levels** classify the severity of a log event so you can filter and alert appropriately.

## Why It Exists
Without levels, important errors drown in debug noise. Levels let you ship verbose logs in dev and only ERROR+ in prod (or sample the rest).

## Common Levels
| Level | Use |
|-------|-----|
| TRACE | Very fine-grained debugging |
| DEBUG | Developer diagnostics |
| INFO | Normal operations / lifecycle |
| WARN | Recoverable / suspicious |
| ERROR | Operation failed |
| FATAL | Unrecoverable; process going down |

## Mapping to OTel
OTel severity numbers map 1–24 (TRACE1..FATAL4). Many platforms align TRACE/DEBUG/INFO/WARN/ERROR/FATAL.

## When to Use Each
- **INFO**: request started/finished, config loaded
- **WARN**: retry, deprecated call, slow downstream
- **ERROR**: caught exception, failed operation
- **DEBUG/TRACE**: only when investigating

## Best Practices
- Don't log errors as INFO
- Sample DEBUG in production (cost)
- Alert on ERROR/FATAL; dashboards on WARN trends

## Related Concepts
- [Structured Logging](structured-logging.md)
- [Log Cost](log-cost.md)
- [OTel Severity](../05-logs/severity.md)
