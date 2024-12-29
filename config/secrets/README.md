# Secrets

There are a few secrets that need to be created in order to allow Argo CD to manage itself and the rest of the applications.

## GitHub

### ApplicationSet

- <https://argo-cd.readthedocs.io/en/stable/operator-manual/applicationset/Generators-Pull-Request/#github>

Argo CD will be polling repositories for pull requests that need ephemeral environments. We need to create a secret to allow Argo CD to authenticate with GitHub to bypass rate limits:

```sh
kubectl create secret generic github-token --from-literal=token="github_pat_XXX" -n argocd
```

TODO: Once the cluster is stable and accessible to the internet, we can leverage [webhooks to trigger Application generation](https://argo-cd.readthedocs.io/en/stable/operator-manual/applicationset/Generators-Pull-Request/#webhook-configuration).

### Notifications

- <https://argo-cd.readthedocs.io/en/stable/operator-manual/notifications/#getting-started>

We also need to create a secret to allow Argo CD notifications to call the GitHub API (which updates deployment statuses)

```sh
kubectl create secret generic argocd-notifications-secret --from-literal=github-token="github_pat_XXX" -n argocd
```
