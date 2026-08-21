# Troubleshooting Quick Reference

Symptom → first place to look.

| Symptom | Check |
|---------|-------|
| No spans | `OTEL_EXPORTER_OTLP_ENDPOINT`, instrumentation present, `debug` exporter |
| Broken traces | W3C propagator, inject/extract on custom transports |
| Collector OOM | add `memory_limiter` **first**, raise limit |
| Dropped data | `otelcol_*_dropped_*`, `send_failed_*` metrics |
| Config won't load | `otelcol --config=... validate` |
| High cost | tail sampling, drop high-card attrs, log sampling |
| Missing errors | tail sampling `status_code: ERROR` policy first |
| Backend auth fail | exporter credentials / token env |

## Health checks
```bash
curl http://collector:13133/healthz
curl http://collector:8888/metrics | grep -E "dropped|send_failed"
```

See [Troubleshooting section](../15-troubleshooting/README.md).
