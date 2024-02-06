# Argo CD application

This Helm Chart will manage all deployed applications and tools.

## Installation

```bash
kubectl apply -f app-of-apps.yaml
```

## Prerequisites

Before instruct Argo CD to check changes in this repository, Argo CD need credentials to access Github repositories and Github packages

Use this template for Github:

```yaml
---
apiVersion: v1
kind: Secret
metadata:
  name: argo-cd-github-rfegolf-es-credentials
  namespace: argo
  labels:
    argocd.argoproj.io/secret-type: repo-creds
stringData:
  url: https://github.com/rfegolf-es
  type: git
  username: <username>
  password: <password> # Github personal access token
```

Use this template for Helm Github Packages:

```yaml
---
apiVersion: v1
kind: Secret
metadata:
  name: argo-cd-oci-github-rfegolf-es-credentials
  namespace: argo
  labels:
    argocd.argoproj.io/secret-type: repo-creds
stringData:
  url: ghcr.io/rfegolf-es
  type: helm
  enableOCI: "true"
  username: <username>
  password: <password> # Github personal access token
```

Aftes this create de App of Apps with `kubectl apply -f app-of-apps.yaml`
