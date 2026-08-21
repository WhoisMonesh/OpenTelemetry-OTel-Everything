# Tutorial: Kubernetes Deployment

Deploy OpenTelemetry on Kubernetes with the Operator: a DaemonSet agent and a gateway.

## 1. Install the Operator
```bash
kubectl apply -f https://github.com/open-telemetry/opentelemetry-operator/releases/latest/download/opentelemetry-operator.yaml
```

## 2. Gateway (central)
```yaml
apiVersion: opentelemetry.io/v1alpha1
kind: OpenTelemetryCollector
metadata: { name: gateway }
spec:
  mode: deployment
  replicas: 2
  config: |
    receivers: { otlp: { protocols: { grpc: {}, http: {} } } }
    processors:
      memory_limiter: { check_interval: 1s, limit_mib: 2000 }
      batch: {}
      tail_sampling:
        policies:
          - { name: errors, type: status_code, status_code: { status_codes: [ERROR] } }
          - { name: prob, type: probabilistic, probabilistic: { sampling_percentage: 10 } }
    exporters: { debug: {} }
    service:
      pipelines:
        traces: { receivers: [otlp], processors: [memory_limiter, batch, tail_sampling], exporters: [debug] }
```

## 3. Agent (per node)
```yaml
apiVersion: opentelemetry.io/v1alpha1
kind: OpenTelemetryCollector
metadata: { name: agent }
spec:
  mode: daemonset
  config: |
    receivers: { otlp: { protocols: { grpc: { endpoint: 0.0.0.0:4317 } } }, hostmetrics: { scrapers: { cpu: {}, memory: {} } } }
    processors: { memory_limiter: { check_interval: 1s, limit_mib: 1000 }, batch: {}, k8sattributes: {} }
    exporters: { otlp/gateway: { endpoint: gateway-collector:4317 } }
    service:
      pipelines:
        traces:  { receivers: [otlp], processors: [memory_limiter, batch, k8sattributes], exporters: [otlp/gateway] }
        metrics: { receivers: [hostmetrics], processors: [memory_limiter, batch, k8sattributes], exporters: [otlp/gateway] }
```

## 4. Auto-instrument an app
```yaml
metadata:
  annotations:
    instrumentation.opentelemetry.io/inject-java: "default"
```

## 5. Verify
```bash
kubectl get opentelemetrycollector
curl http://<gateway-pod>:13133/healthz
```

See [Kubernetes Deployment section](../../13-kubernetes-deployment/README.md).
