# Sampling Loss

## Symptom
Expected traces/spans are missing — you sampled them away.

## Likely Causes & Fixes
| Cause | Fix |
|-------|-----|
| Head sampling too aggressive | Raise SDK/probabilistic percentage |
| Tail sampling missing policy | Ensure a fallback probabilistic policy |
| Errors being dropped | Add `status_code: ERROR` policy **first** |
| Wrong policy order | Order matters; errors before probabilistic |
| Async spans sampled independently | Use Links / propagate context |

## Tail Sampling Example (keep errors)
```yaml
processors:
  tail_sampling:
    policies:
      - { name: errors, type: status_code, status_code: { status_codes: [ERROR] } }
      - { name: prob, type: probabilistic, probabilistic: { sampling_percentage: 10 } }
```

## Best Practices
- Always keep 100% of errors
- Have a fallback probabilistic policy (else unwanted drops)
- Use head sampling to reduce agent load, tail for smart keep

## Related Concepts
- [Sampling](../02-architecture/sampling.md)
- [Missing Spans](missing-spans.md)
