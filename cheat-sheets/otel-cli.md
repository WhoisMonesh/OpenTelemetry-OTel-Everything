# otelcli Cheatsheet

`otelcli` is a small CLI to send traces/metrics/logs via OTLP — great for testing pipelines.

## Install
```bash
go install github.com/equinix-labs/otel-cli@latest
# or brew install otel-cli
```

## Send a span
```bash
otelcli span --service checkout --name "test-op" \
  --endpoint http://localhost:4317 --protocol grpc \
  --attrs "http.method=GET,http.route=/health"
```

## Send a metric
```bash
otelcli metric --service checkout --name requests --value 1
```

## Send a log
```bash
otelcli log --service checkout --severity info --message "hello otel"
```

## Use Cases
- Smoke-test a Collector pipeline
- Verify propagation/exporters
- Teaching / demos

See [Collector Config Cheatsheet](collector-config.md) and [Exporters](../02-architecture/exporters.md).
