---
description: Install, upgrade, or remove OTel Benchmark App on Kubernetes using the Helm chart from the Dynatrace registry
argument-hint: [install|upgrade|uninstall]
---

Perform the requested Helm lifecycle action for OTel Benchmark App based on $ARGUMENTS (default to
`install` if not specified). The chart is published at
`oci://europe-docker.pkg.dev/dynatrace-demoability/helm/easytrade`.

## Install
```bash
helm install easytrade oci://europe-docker.pkg.dev/dynatrace-demoability/helm/easytrade \
  --create-namespace --namespace otel-benchmark-app
```

## Upgrade
```bash
helm upgrade easytrade oci://europe-docker.pkg.dev/dynatrace-demoability/helm/easytrade \
  --namespace otel-benchmark-app
```

## Uninstall
```bash
helm uninstall otel-benchmark-app -n otel-benchmark-app
# optionally delete the namespace too
kubectl delete namespace otel-benchmark-app
```

After install or upgrade, verify the deployment:
```bash
kubectl get pods -n otel-benchmark-app
kubectl get svc -n otel-benchmark-app
```
All 19 services should reach `Running` state. The app is available at the cluster ingress IP on port 80.

Then apply the Dynatrace Monaco configuration to wire up business events, dashboards, and alerting — see `./monaco/README.md` for instructions.
