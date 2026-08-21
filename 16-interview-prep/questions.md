# Common Interview Questions

## Q1: OpenTracing vs OpenCensus vs OpenTelemetry?
**A:** OpenTracing = tracing API; OpenCensus = metrics+tracing (Google). They merged into OpenTelemetry, which adds logs, a Collector, and a standard protocol (OTLP).

## Q2: What is OTLP and why does it matter?
**A:** OTLP is the standard OTel wire protocol (gRPC/HTTP). It decouples SDKs from backends so you can switch destinations by changing the Collector config only.

## Q3: API vs SDK?
**A:** API is the interface apps call (no overhead); SDK is the implementation (records, batches, samples, exports). Apps depend on the API; operators configure the SDK.

## Q4: Head vs tail sampling?
**A:** Head sampling decides at ingest (cheap, random); tail sampling decides after the whole trace is seen (smart — keep errors/slow). Use head at SDK, tail at gateway.

## Q5: How does distributed tracing work across services?
**A:** The active SpanContext is injected into outgoing requests (W3C `traceparent`) and extracted by the receiving service, creating child spans in one trace.

## Q6: How do you control cost?
**A:** Head + tail sampling, drop high-cardinality attributes (Views/processor), sample logs, tier retention. Keep 100% of errors.

## Q7: How do you correlate logs and traces?
**A:** Attach `trace_id`/`span_id` to log records; enabled via appenders/bridges. Then jump from a trace to its logs in the backend.

## Q8: What is a Connector?
**A:** A Collector component that consumes one signal and produces another — e.g., `spanmetrics` generates RED metrics from traces.

## Q9: How do you deploy OTel on Kubernetes?
**A:** OpenTelemetry Operator or Helm: DaemonSet agent (light) + Deployment gateway (heavy, tail sampling, exporters). Use `k8sattributes` and auto-instrumentation injection.

## Q10: What's the fourth signal?
**A:** Profiling (continuous), still experimental in OTel — sampling where CPU/memory is spent, correlated with traces.

## Related Concepts
- [Core Concepts](concepts.md)
- [Cheatsheet](cheatsheet.md)
