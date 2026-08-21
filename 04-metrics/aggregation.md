# Aggregation

## What It Is
**Aggregation** defines how individual measurements are combined into the data points exported for a metric stream (sum, last-value, histogram, etc.).

## Why It Exists
The SDK must decide how to turn many `record()` calls into compact, backend-friendly points. Aggregation is that policy.

## Aggregation Types
| Aggregation | Output |
|-------------|--------|
| `Sum` | Total (monotonic or not) |
| `LastValue` | Most recent value (gauges) |
| `ExplicitBucketHistogram` | Buckets + sum + count |
| `Base2ExponentialHistogram` | Efficient, adaptive buckets |
| `Drop` | No data exported |

## Architecture
```mermaid
graph LR
    Rec[record(120)] --> Agg[Aggregation]
    Agg --> Pt[Data point: bucket counts]
```

## When to Use It
- Histograms for latency (default)
- `Drop` to disable an instrument via View
- Exponential histograms for wide value ranges

## Code Example
Configure via Views (see [Views](views.md)):
```yaml
# Collector transform/aggregation examples are backend-side
```

## Best Practices
- Use exponential histograms when value range is unknown
- Match histogram boundaries to SLO thresholds
- Avoid `Drop` unless intentionally disabling

## Related Concepts
- [Views](views.md)
- [Histogram](histogram.md)
- [Metric Streams](metric-streams.md)
