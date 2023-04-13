Save this file as `bootstrap.yaml`:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  annotations:
    argocd.argoproj.io/tracking-id: argocd:argoproj.io/Application:argocd/bootstrap
  name: bootstrap
  namespace: argocd
spec:
  destination:
    name: in-cluster
    namespace: argocd
  project: default
  source:
    path: prod/bootstrap/local
    repoURL: https://github.com/Calchan/monorepo-local.git
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
```

Then:

```kubectl -n argocd apply -f bootstrap.yaml```
