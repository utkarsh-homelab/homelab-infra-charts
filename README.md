# homelab-infra-charts

Vendored Helm charts for homelab Kubernetes cluster.

## Structure

```
charts/
├── argocd/                           → argo-cd (v9.7.0, app v3.4.4)
├── metallb/                          → metallb (v0.16.1, app v0.14.9)
├── traefik/                          → traefik (v41.0.0, app v3.7.5)
├── cert-manager/                     → cert-manager (v1.17.0, app v1.17.0)
├── csi-driver-nfs/                   → csi-driver-nfs (v4.13.3)
├── tenant-rbac/                      → tenant-rbac (v1.0.0)
├── kube-prometheus-stack/            → kube-prometheus-stack (v87.1.0, app v0.92.0)
├── alertmanager-discord-webhook/     → alertmanager-discord-webhook (v1.0.0)
├── local-path-provisioner/           → local-path-provisioner (v0.0.37)
├── strimzi-kafka/                    → strimzi-kafka-operator (v0.46.1)
├── kafka-cluster/                    → standalone (Kafka KRaft single-node)
├── cloudnative-pg/                   → cloudnative-pg (v1.30.0, chart v0.29.0)
└── postgres-cluster/                 → standalone (PostgreSQL 16 single-node)
```

Each chart is an umbrella chart with a single upstream dependency. 

Run the following before deploying:
```bash
# Add upstream Helm repo
helm repo add <component-name> <helm-chart-url>

# Download sub-chart dependencies
helm dependency build charts/<name>
```

## Upstream Charts

- ArgoCD : [Chart](https://artifacthub.io/packages/helm/argo/argo-cd), [Docs](https://argo-cd.readthedocs.io/en/stable/user-guide/helm/), [Source Code](https://github.com/argoproj/argo-helm/tree/main/charts/argo-cd)
- CSI Driver NFS : [Chart](https://artifacthub.io/packages/helm/csi-driver-nfs/csi-driver-nfs), [Source Code](https://github.com/kubernetes-csi/csi-driver-nfs)
- MetalLB : [Chart](https://artifacthub.io/packages/helm/metallb/metallb), [Docs](https://metallb.universe.tf/installation/), [Source Code](https://github.com/metallb/metallb)
- Traefik : [Chart](https://artifacthub.io/packages/helm/traefik/traefik), [Docs](https://doc.traefik.io/traefik/getting-started/), [Source Code](https://github.com/traefik/traefik-helm-chart)
- Cert Manager : [Chart](https://artifacthub.io/packages/helm/cert-manager/cert-manager), [Docs](https://cert-manager.io/docs/installation/helm/), [Source Code](https://github.com/cert-manager/cert-manager)
- Kube Prometheus Stack : [Chart](https://artifacthub.io/packages/helm/prometheus-community/kube-prometheus-stack),  [Source Code](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack)
- Local Path Provisioner : [Chart](https://artifacthub.io/packages/helm/rancher-local-path-provisioner/local-path-provisioner), [Source Code](https://github.com/rancher/local-path-provisioner)
- Strimzi Kafka Operator : [Chart](https://artifacthub.io/packages/helm/strimzi/strimzi-kafka-operator), [Docs](https://strimzi.io/docs/operators/latest/), [Source Code](https://github.com/strimzi/strimzi-kafka-operator)
- CloudNativePG Operator : [Chart](https://artifacthub.io/packages/helm/cloudnative-pg/cloudnative-pg), [Docs](https://cloudnative-pg.io/documentation/), [Source Code](https://github.com/cloudnative-pg/charts)

## Companion Repo

Continuous deployment (CD) is Handled by ArgoCD, refer to the GitOps repo here : [homelab-gitops](https://github.com/utkarsh-homelab/homelab-gitops)