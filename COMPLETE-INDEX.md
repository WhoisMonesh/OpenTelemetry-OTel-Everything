# COMPLETE INDEX — OTEL Related

An exhaustive categorized index of every OpenTelemetry concept, component, tool, and pattern covered in this repository.

> **Totals:** 21 topic categories + cheat-sheets + docs + examples = **220 documents**. Logging-focused sections 18–21 cover Kibana/Elastic and Coralogix in depth.

---

## 01 · Core Concepts (15)
| File | Concept |
|------|---------|
| [what-is-opentelemetry.md](01-core-concepts/what-is-opentelemetry.md) | Definition, history, CNCF, scope |
| [observability.md](01-core-concepts/observability.md) | Observability vs monitoring, pillars |
| [signals.md](01-core-concepts/signals.md) | Traces, Metrics, Logs, Profiles |
| [otlp.md](01-core-concepts/otlp.md) | OpenTelemetry Protocol |
| [telemetry-data-model.md](01-core-concepts/telemetry-data-model.md) | Resource/Scope/Entity model |
| [api-vs-sdk.md](01-core-concepts/api-vs-sdk.md) | API (interface) vs SDK (impl) |
| [resource.md](01-core-concepts/resource.md) | Entity producing telemetry |
| [attributes.md](01-core-concepts/attributes.md) | Key-value metadata |
| [instrumentation.md](01-core-concepts/instrumentation.md) | Manual vs auto |
| [auto-instrumentation.md](01-core-concepts/auto-instrumentation.md) | Zero-code agents |
| [exporter.md](01-core-concepts/exporter.md) | Sending telemetry |
| [semantic-conventions.md](01-core-concepts/semantic-conventions.md) | Standard attribute names |
| [context.md](01-core-concepts/context.md) | Context propagation primitive |
| [stability-levels.md](01-core-concepts/stability-levels.md) | Stable/RC/Experimental |

## 02 · Architecture (10)
[README](02-architecture/README.md) · [collector-pipeline.md](02-architecture/collector-pipeline.md) · [agent-vs-gateway.md](02-architecture/agent-vs-gateway.md) · [receivers.md](02-architecture/receivers.md) · [processors.md](02-architecture/processors.md) · [exporters.md](02-architecture/exporters.md) · [connectors.md](02-architecture/connectors.md) · [extensions.md](02-architecture/extensions.md) · [sampling.md](02-architecture/sampling.md) · [deployment-modes.md](02-architecture/deployment-modes.md)

## 03 · Traces (11)
[README](03-traces/README.md) · [span.md](03-traces/span.md) · [span-context.md](03-traces/span-context.md) · [parent-child.md](03-traces/parent-child.md) · [attributes-and-events.md](03-traces/attributes-and-events.md) · [links.md](03-traces/links.md) · [span-status.md](03-traces/span-status.md) · [distributed-tracing.md](03-traces/distributed-tracing.md) · [trace-id-correlation.md](03-traces/trace-id-correlation.md) · [context-propagation-traces.md](03-traces/context-propagation-traces.md) · [tracing-best-practices.md](03-traces/tracing-best-practices.md)

## 04 · Metrics (11)
[README](04-metrics/README.md) · [counter.md](04-metrics/counter.md) · [gauge.md](04-metrics/gauge.md) · [histogram.md](04-metrics/histogram.md) · [async-instruments.md](04-metrics/async-instruments.md) · [views.md](04-metrics/views.md) · [aggregation.md](04-metrics/aggregation.md) · [exemplars.md](04-metrics/exemplars.md) · [metric-streams.md](04-metrics/metric-streams.md) · [metric-best-practices.md](04-metrics/metric-best-practices.md) · [metric-stability.md](04-metrics/metric-stability.md)

## 05 · Logs (10)
[README](05-logs/README.md) · [log-record.md](05-logs/log-record.md) · [severity.md](05-logs/severity.md) · [log-attributes.md](05-logs/log-attributes.md) · [log-sdk.md](05-logs/log-sdk.md) · [bridging.md](05-logs/bridging.md) · [log-appenders.md](05-logs/log-appenders.md) · [log-correlation.md](05-logs/log-correlation.md) · [log-best-practices.md](05-logs/log-best-practices.md) · [log-stability.md](05-logs/log-stability.md)

## 06 · Collector (9)
[README](06-collector/README.md) · [otelcol.md](06-collector/otelcol.md) · [config.md](06-collector/config.md) · [distributions.md](06-collector/distributions.md) · [processors-deep.md](06-collector/processors-deep.md) · [exporters-deep.md](06-collector/exporters-deep.md) · [scaling.md](06-collector/scaling.md) · [observability-of-collector.md](06-collector/observability-of-collector.md) · [security.md](06-collector/security.md)

## 07 · Context Propagation (7)
[README](07-context-propagation/README.md) · [trace-context.md](07-context-propagation/trace-context.md) · [baggage.md](07-context-propagation/baggage.md) · [propagators.md](07-context-propagation/propagators.md) · [b3.md](07-context-propagation/b3.md) · [composite-propagators.md](07-context-propagation/composite-propagators.md) · [cross-process.md](07-context-propagation/cross-process.md)

## 08 · Instrumentation (9)
[README](08-instrumentation/README.md) · [manual.md](08-instrumentation/manual.md) · [auto-zero-code.md](08-instrumentation/auto-zero-code.md) · [libraries.md](08-instrumentation/libraries.md) · [web.md](08-instrumentation/web.md) · [mobile.md](08-instrumentation/mobile.md) · [ebpf.md](08-instrumentation/ebpf.md) · [instrumentation-best-practices.md](08-instrumentation/instrumentation-best-practices.md) · [migration.md](08-instrumentation/migration.md)

## 09 · Language SDKs (11)
[README](09-language-sdks/README.md) · [go.md](09-language-sdks/go.md) · [python.md](09-language-sdks/python.md) · [java.md](09-language-sdks/java.md) · [js-ts.md](09-language-sdks/js-ts.md) · [dotnet.md](09-language-sdks/dotnet.md) · [rust.md](09-language-sdks/rust.md) · [cpp.md](09-language-sdks/cpp.md) · [ruby.md](09-language-sdks/ruby.md) · [php.md](09-language-sdks/php.md) · [stability-matrix.md](09-language-sdks/stability-matrix.md)

## 10 · Exporters & Backends (12)
[README](10-exporters-backends/README.md) · [jaeger.md](10-exporters-backends/jaeger.md) · [tempo.md](10-exporters-backends/tempo.md) · [prometheus.md](10-exporters-backends/prometheus.md) · [loki.md](10-exporters-backends/loki.md) · [grafana.md](10-exporters-backends/grafana.md) · [honeycomb.md](10-exporters-backends/honeycomb.md) · [lightstep.md](10-exporters-backends/lightstep.md) · [datadog.md](10-exporters-backends/datadog.md) · [newrelic.md](10-exporters-backends/newrelic.md) · [elastic.md](10-exporters-backends/elastic.md) · [signalfx-splunk.md](10-exporters-backends/signalfx-splunk.md)

## 11 · Semantic Conventions (11)
[README](11-semantic-conventions/README.md) · [resource.md](11-semantic-conventions/resource.md) · [http.md](11-semantic-conventions/http.md) · [db.md](11-semantic-conventions/db.md) · [messaging.md](11-semantic-conventions/messaging.md) · [rpc.md](11-semantic-conventions/rpc.md) · [faas.md](11-semantic-conventions/faas.md) · [system.md](11-semantic-conventions/system.md) · [k8s.md](11-semantic-conventions/k8s.md) · [exceptions.md](11-semantic-conventions/exceptions.md) · [stability.md](11-semantic-conventions/stability.md)

## 12 · Profiling (6)
[README](12-profiling/README.md) · [continuous-profiling.md](12-profiling/continuous-profiling.md) · [pprof.md](12-profiling/pprof.md) · [ebpf-profiling.md](12-profiling/ebpf-profiling.md) · [otlp-profiles.md](12-profiling/otlp-profiles.md) · [flamegraphs.md](12-profiling/flamegraphs.md)

## 13 · Kubernetes Deployment (9)
[README](13-kubernetes-deployment/README.md) · [operator.md](13-kubernetes-deployment/operator.md) · [helm.md](13-kubernetes-deployment/helm.md) · [daemonset-agent.md](13-kubernetes-deployment/daemonset-agent.md) · [gateway.md](13-kubernetes-deployment/gateway.md) · [otel-crds.md](13-kubernetes-deployment/otel-crds.md) · [auto-instrumentation-k8s.md](13-kubernetes-deployment/auto-instrumentation-k8s.md) · [sidecar-vs-daemonset.md](13-kubernetes-deployment/sidecar-vs-daemonset.md) · [best-practices-k8s.md](13-kubernetes-deployment/best-practices-k8s.md)

## 14 · Observability Practice (7)
[README](14-observability-practice/README.md) · [golden-signals.md](14-observability-practice/golden-signals.md) · [red-use.md](14-observability-practice/red-use.md) · [slos.md](14-observability-practice/slos.md) · [alerting.md](14-observability-practice/alerting.md) · [cost.md](14-observability-practice/cost.md) · [opentelemetry-demo.md](14-observability-practice/opentelemetry-demo.md) · [incident-response.md](14-observability-practice/incident-response.md)

## 15 · Troubleshooting (8)
[README](15-troubleshooting/README.md) · [missing-spans.md](15-troubleshooting/missing-spans.md) · [dropped-data.md](15-troubleshooting/dropped-data.md) · [oom.md](15-troubleshooting/oom.md) · [sampling-loss.md](15-troubleshooting/sampling-loss.md) · [collector-errors.md](15-troubleshooting/collector-errors.md) · [propagation-gaps.md](15-troubleshooting/propagation-gaps.md) · [runbooks.md](15-troubleshooting/runbooks.md)

## 16 · Interview Prep (6)
[README](16-interview-prep/README.md) · [concepts.md](16-interview-prep/concepts.md) · [questions.md](16-interview-prep/questions.md) · [cheatsheet.md](16-interview-prep/cheatsheet.md) · [learning-path.md](16-interview-prep/learning-path.md) · [glossary.md](16-interview-prep/glossary.md)

## 17 · Company Cases (7)
[README](17-company-cases/README.md) · [adoption.md](17-company-cases/adoption.md) · [migrations.md](17-company-cases/migrations.md) · [lessons-learned.md](17-company-cases/lessons-learned.md) · [case-ecommerce.md](17-company-cases/case-ecommerce.md) · [case-fintech.md](17-company-cases/case-fintech.md) · [case-platform.md](17-company-cases/case-platform.md)

## 18 · Logging Essentials (12)
[README](18-logging-essentials/README.md) · [structured-logging.md](18-logging-essentials/structured-logging.md) · [log-levels.md](18-logging-essentials/log-levels.md) · [log-formats.md](18-logging-essentials/log-formats.md) · [centralized-logging.md](18-logging-essentials/centralized-logging.md) · [log-shipping.md](18-logging-essentials/log-shipping.md) · [agents.md](18-logging-essentials/agents.md) · [parsing.md](18-logging-essentials/parsing.md) · [enrichment.md](18-logging-essentials/enrichment.md) · [indexing.md](18-logging-essentials/indexing.md) · [retention.md](18-logging-essentials/retention.md) · [log-cost.md](18-logging-essentials/log-cost.md)

## 19 · Kibana & the Elastic Stack (14)
[README](19-kibana-elastic/README.md) · [elasticsearch.md](19-kibana-elastic/elasticsearch.md) · [kibana-ui.md](19-kibana-elastic/kibana-ui.md) · [ecs.md](19-kibana-elastic/ecs.md) · [discover.md](19-kibana-elastic/discover.md) · [dashboards-visualizations.md](19-kibana-elastic/dashboards-visualizations.md) · [alerts.md](19-kibana-elastic/alerts.md) · [ilm.md](19-kibana-elastic/ilm.md) · [data-streams.md](19-kibana-elastic/data-streams.md) · [ingest-pipelines.md](19-kibana-elastic/ingest-pipelines.md) · [beats.md](19-kibana-elastic/beats.md) · [elastic-agent-fleet.md](19-kibana-elastic/elastic-agent-fleet.md) · [otlp-in-elastic.md](19-kibana-elastic/otlp-in-elastic.md) · [integrations.md](19-kibana-elastic/integrations.md)

## 20 · Coralogix (13)
[README](20-coralogix/README.md) · [platform-overview.md](20-coralogix/platform-overview.md) · [tco-optimizer.md](20-coralogix/tco-optimizer.md) · [parsing-rules.md](20-coralogix/parsing-rules.md) · [loggregation.md](20-coralogix/loggregation.md) · [anomalies.md](20-coralogix/anomalies.md) · [alerts.md](20-coralogix/alerts.md) · [grafana-integration.md](20-coralogix/grafana-integration.md) · [otlp-coralogix.md](20-coralogix/otlp-coralogix.md) · [query-dataflow.md](20-coralogix/query-dataflow.md) · [integrations-coralogix.md](20-coralogix/integrations-coralogix.md) · [log-archiving.md](20-coralogix/log-archiving.md) · [use-cases.md](20-coralogix/use-cases.md)

## 21 · Log Observability Practice (7)
[README](21-log-observability-practice/README.md) · [query-languages.md](21-log-observability-practice/query-languages.md) · [log-based-slos.md](21-log-observability-practice/log-based-slos.md) · [troubleshooting-with-logs.md](21-log-observability-practice/troubleshooting-with-logs.md) · [incident-response-logs.md](21-log-observability-practice/incident-response-logs.md) · [log-security.md](21-log-observability-practice/log-security.md) · [cost-governance.md](21-log-observability-practice/cost-governance.md)

## Cheat Sheets (6)
[collector-config.md](cheat-sheets/collector-config.md) · [env-vars.md](cheat-sheets/env-vars.md) · [otel-cli.md](cheat-sheets/otel-cli.md) · [receiver-exporter-matrix.md](cheat-sheets/receiver-exporter-matrix.md) · [semantic-conventions-quick.md](cheat-sheets/semantic-conventions-quick.md) · [troubleshooting-quick.md](cheat-sheets/troubleshooting-quick.md)

## Docs (3)
[otlp-specification.md](docs/otlp-specification.md) · [version-stability.md](docs/version-stability.md) · [cloud-integrations.md](docs/cloud-integrations.md)

## Examples (3)
[tutorials/tutorial-local-quickstart.md](examples/tutorials/tutorial-local-quickstart.md) · [tutorials/tutorial-kubernetes.md](examples/tutorials/tutorial-kubernetes.md) · [common-patterns/example-collector-configs.md](examples/common-patterns/example-collector-configs.md)

---

*Inspired by the structure of [K8S-Everything](https://github.com/WhoisMonesh/K8S-Everything).*
