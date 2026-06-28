# homelab-infra-charts

Vendored Helm charts for homelab Kubernetes cluster.

## Structure

```
charts/
├── argocd/                  → argo-cd (v9.7.0, app v3.4.4)
├── metallb/                 → metallb (v0.16.1, app v0.14.9)
├── traefik/                 → traefik (v41.0.0, app v3.7.5)
├── cert-manager/            → cert-manager (v1.17.0, app v1.17.0)
└── csi-driver-nfs/          → csi-driver-nfs (v4.13.3)
```

Each chart is an umbrella chart with a single upstream dependency. 

Run the following before deploying:
```bash
# Add upstream Helm repo
helm repo add <component-name> <helm-chart-url>

# Download sub-chart dependencies
helm dependency build charts/<name>
```

## Companion Repo

Continuous deployment (CD) is Handled by ArgoCD, refer to the GitOps repo here : [homelab-gitops](https://github.com/utkarsh-homelab/homelab-gitops)