# Semantic Conventions Quick Reference

Frequently used standard attribute keys. Prefer these over custom names.

## Resource
- `service.name`, `service.version`, `service.namespace`
- `deployment.environment`
- `cloud.provider`, `cloud.region`, `cloud.account.id`
- `host.name`, `host.arch`
- `k8s.cluster.name`, `k8s.namespace.name`, `k8s.pod.name`, `k8s.node.name`

## HTTP
- `http.request.method`, `http.route`, `http.response.status_code`
- `url.full`, `server.address`, `server.port`
- `client.address`, `network.protocol.version`

## DB
- `db.system`, `db.name`, `db.operation`, `db.statement`, `db.collection.name`

## Messaging
- `messaging.system`, `messaging.destination.name`, `messaging.operation`

## RPC
- `rpc.system`, `rpc.service`, `rpc.method`, `rpc.grpc.status_code`

## Errors
- `exception.type`, `exception.message`, `exception.stacktrace`, `error.type`

## Tips
- Use the semconv **library constants**, not raw strings
- Some keys renamed (e.g., `http.method` → `http.request.method`); pin versions

See [Semantic Conventions section](../11-semantic-conventions/README.md).
