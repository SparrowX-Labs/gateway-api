# Development Gateway API values

Each YAML file in this directory contains values for one service. Do not put
Kubernetes manifests here. The reusable Gateway API Helm chart renders the
shared `GatewayClass` and `Gateway`, then creates an `HTTPRoute` for each
values file.

Add a new service by adding another values-only YAML file. Argo CD uses the
`dev/*.yaml` glob, so the new file is picked up automatically.

Minimal example:

```yaml
apis:
  task-api:
    routeName: task-api
    backendService: task-api
    path: /api/tasks
    servicePort: 80
```

The chart requires `routeName`, `backendService`, `path`, and `servicePort`.
The hostname can be supplied per service; namespace, Gateway, listener, and
path type come from the shared Gateway configuration or chart defaults.
