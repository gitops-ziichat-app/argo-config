# Config Maps

Notable configurations for the project.

## argocd-cm.yaml

- <https://argo-cd.readthedocs.io/en/stable/user-guide/kustomize/#kustomizing-helm-charts>
- <https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Controlling-Resource-Modification/#ignore-certain-changes-to-applications>
- <https://argo-cd.readthedocs.io/en/latest/user-guide/resource_tracking/#choosing-a-tracking-method>

## argocd-cmd-params-cm.yaml

- <https://argo-cd.readthedocs.io/en/latest/operator-manual/applicationset/Generators-Git-File-Globbing/>

## argocd-notifications-cm.yaml

- <https://argo-cd.readthedocs.io/en/latest/operator-manual/notifications/>

  Be sure to update the `argocd-notifications-secret` with `github-token`.
