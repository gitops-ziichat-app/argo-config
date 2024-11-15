# Argo CD Configuration

[Argo CD](https://argo-cd.readthedocs.io/en/stable/) is a declarative, GitOps continuous delivery tool for Kubernetes. This repository contains the configuration for Argo, as [apps of apps](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-bootstrapping/), so that we can bootstrap the Argo CD installation to manage itself.

## Usage

<https://argo-cd.readthedocs.io/en/stable/understand_the_basics/>

### Bootstrap

<https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd>

```sh
# Install ArgoCD
kubectl apply -k argo/overlay

# Instruct ArgoCD to manage itself via GitOps
kubectl apply -f ./config/application.yaml

# Give ArgoCD an App of apps to manage via GitOps
kubectl apply -f ./app-of-apps/application.yaml

# TODO: Add Gateway API setup
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

<https://localhost> will provide the Argo CD UI.

### Configuration

Argo CD applications, projects and settings can be defined declaratively using Kubernetes manifests.

<https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/>

- Add your applications to the [app-of-apps](./app-of-apps/) directory
- Add applications, projects and settings to the [config](./config/) directory
