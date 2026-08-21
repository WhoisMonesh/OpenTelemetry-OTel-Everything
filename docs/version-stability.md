# Version & Stability

How OpenTelemetry versions and stability levels work.

## Stability Levels
| Level | Guarantee |
|-------|-----------|
| **Stable** | Backward compatible; safe for production |
| **Candidate (RC)** | Feature-complete, pending stabilization |
| **Experimental** | May change; opt-in |

## Current Stable Signals
- **Traces**: Stable (since 1.0)
- **Metrics**: Stable (since metrics GA)
- **Logs**: Stable (logs GA)
- **Profiles**: Experimental (emerging)

## Release Cadence
- Per-language SDKs release independently (semver)
- Collector (contrib) releases frequently
- Spec/semconv versioned separately

## Versioning Notes
- Language SDKs follow semver; minor bumps may add (not break) stable APIs
- Experimental features may be removed/changed between minors
- Semantic conventions can be renamed (e.g., `http.method` → `http.request.method`)

## Best Practices
- Pin SDK and Collector versions
- Build on Stable APIs only
- Watch release notes for promotions/demotions

See [Stability Levels (core)](../01-core-concepts/stability-levels.md) and [Language Stability Matrix](../09-language-sdks/stability-matrix.md).
