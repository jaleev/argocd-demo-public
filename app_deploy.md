# Different methods to deploy applicaiton

## UI


## CMD
```bash
argocd app create <application_name> --repo <code_repo> --revision <branch_name> --path <path_in_branch> --dest-server https://kubernetes.default.svc --dest-namespace <namespace> 

argocd app sync application_name
```

## Application manifest

```bash
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: devapp2
  namespace: argocd
  labels:
    name: devapp2
spec:
  project: default
  source:
    repoURL: https://github.com/mialeevs/argocd-demo-public.git
    targetRevision: lab 
    path: apptwo
  destination:
    server: https://kubernetes.default.svc
    namespace: devapp2
  syncPolicy:
    automated: 
      prune: true
      selfHeal: true

```
