# homelab-infra-charts

Vendored Helm charts for homelab Kubernetes cluster.

## Structure

```
charts/
└── argocd/                  → argo-cd (v9.7.0, app v3.4.4)
```

Each chart is an umbrella chart with a single upstream dependency. Run
`helm dependency build charts/<name>` before deploying.
