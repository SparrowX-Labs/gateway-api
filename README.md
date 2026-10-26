# Gateway API resources

This repository contains the environment-specific Gateway API resources
managed by Argo CD.

```text
  dev/
    <service-name>.yaml
  prod/
    <service-name>.yaml
```

Each service file contains values only. The reusable Helm chart owns shared
resources such as `GatewayClass` and `Gateway`, and generates one `HTTPRoute`
per values file. This environment uses Traefik's Gateway API implementation.

The development Argo CD application reads `dev/*.yaml`; create a separate
production application reading `prod/*.yaml`.
