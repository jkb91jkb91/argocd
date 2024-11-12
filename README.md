


1. Installation argocd CLI/ argo in cluster / namespace argocd   
2. Connect repo (easy version) -not recommended  






# Installation argocd CLI/ argo in cluster / namespace argocd  
Install argocd CLI
```
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
```
Create ns argocd  
```
kubectl create ns argocd
```
Install argo in kubernetes  
```
kubectl apply -f  https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml -n argocd
```

# Connect repo (easy version) -not recommended   
```
argocd repo add https://github.com/jkb91jkb91/argocd --username jkb91jkb91 --password TOKEN
```
production
path apps/apache/production #kustomization.yaml inside  
```
argocd app create apache --repo https://github.com/jkb91jkb91/argocd --path apps/apache/production --dest-server https://kubernetes.default.svc --dest-namespace production
```

staging
path apps/apache/staging #kustomization.yaml inside  
```
argocd app create apache-staging --repo https://github.com/jkb91jkb91/argocd --path apps/apache/staging --dest-server https://kubernetes.default.svc --dest-namespace staging
```
