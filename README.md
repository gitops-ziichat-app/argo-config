# Argo CD Configuration

[Argo CD](https://argo-cd.readthedocs.io/en/stable/) is a declarative, GitOps continuous delivery tool for Kubernetes. This repository contains the configuration for Argo, as [apps of apps](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-bootstrapping/), so that we can bootstrap the Argo CD installation to manage itself.

## Usage

<https://argo-cd.readthedocs.io/en/stable/understand_the_basics/>

### Bootstrap

The [argo](./argo/) directory contains the installation files for Argo CD.

<https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd>

```sh
# Install ArgoCD
kubectl apply -k argo/overlay

# Instruct ArgoCD to manage itself via GitOps
kubectl apply -f ./config/application.yaml

# Give ArgoCD an application to manage the rest of the applications via AoA
kubectl apply -f ./app-of-apps/application.yaml

# TODO: Add Gateway API setup
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

<https://localhost> will provide the Argo CD UI.

### Configuration

The [config](./config/) directory contains the configuration for Argo CD.

Argo CD applications, projects and settings can be defined declaratively using Kubernetes manifests.

<https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/>

### Applications

The [app-of-apps](./app-of-apps/) directory contains the configuration for the Argo CD AoA that manages the rest of the applications.

Add [addons](./app-of-apps/addons/application-sets) to enable additional functionality for Kubernetes clusters. [clusters](./app-of-apps/clusters/) added will have all addons installed automatically. [environments](./app-of-apps/environments/) can be added to provide common settings across clusters.

Add [apps](./app-of-apps/apps/application-sets) to deploy user space applications to the Kubernetes clusters.
