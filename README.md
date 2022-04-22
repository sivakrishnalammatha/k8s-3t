# 3t

Examples of K8s deployments 3 tier app.

### Raw manifests
```
kubectl apply -f manifests/mysql
kubectl apply -f manifests/django
kubectl apply -f manifests/varnish
```

### Helm
```
helmfile -l stage=mysql -f helm/helmfile.yaml apply
helmfile -l stage=django -f helm/helmfile.yaml apply
helmfile -l stage=varnish -f helm/helmfile.yaml apply
```
### Kustomize
```
kustomize build kustomize/varnish/overlays/dev/ | kubectl apply -f -
kustomize build kustomize/django/overlays/dev/ | kubectl apply -f -
kustomize build kustomize/mysql/overlays/dev/ | kubectl apply -f -
```