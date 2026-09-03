---
description: Deploy, upgrade, or remove OTel Benchmark App on Kubernetes using the Helm chart from the Dynatrace registry
---

# OTel Benchmark App Helm Deploy

EasyTrade publishes a Helm chart to `oci://europe-docker.pkg.dev/dynatrace-demoability/helm/easytrade`.

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

## Verify deployment

```bash
kubectl get pods -n otel-benchmark-app
kubectl get svc -n otel-benchmark-app
```

All 19 services should reach `Running` state. App is available at the cluster ingress IP on port 80.

## Dynatrace configuration

Apply Monaco configuration after deploy:
```bash
# See ./monaco/README.md for full instructions
```

Monaco configs live in `./monaco/`. Apply them to wire up business events, dashboards, and alerting.
