# The package manager for kubernetes

## Three Big Concepts
- A Chart is a Helm package.
- A Repository is the place where charts can be collected and shared. It's like Perl's CPAN archive or the Fedora Package Database, but for Kubernetes packages.- A Release is an instance of a chart running in a Kubernetes cluster.

## Quickstart

install helm

helm search
```
helm search hub
helm search repo
```

Initialize a Helm Chart Repository

```
helm repo add bitnami https://charts.bitnami.com/bitnami
```

## helm tips

### install 加上 --dry-run



## helm features
- pure client tools (v3)
  - w/o tiller
  - don't need helm init
- 3-way merge
- helm template
  - values.yaml
- dependency

## hub
- more then helm

## repo

## charts

### chart hooks
- (pre/post)-(install/delete/upgrade/rollback) / test


## helm plugins
https://helm.sh/docs/community/related/#helm-plugins
### helm secrets / diff /  git
https://www.youtube.com/watch?v=FriVNkaEU8Q
sops 

### 

## web ui
- kubeapps
  - https://kubeapps.dev/docs/latest/tutorials/getting-started/#step-1-install-kubeapps
  - kubectl port-forward --address=100.115.92.200 -n kubeapps svc/kubeapps 8080:80 
- helm-dashboard


## tilt / werf

## flux / argocd
- helm operator


## keptn

## GitOps


## argo workflow / 
