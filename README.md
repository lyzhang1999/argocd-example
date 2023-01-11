## create cluster

1. kind create cluster --config kind/config.yaml

## install ingress-nginx

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

backup: https://raw.githubusercontent.com/argoproj/argo-cd/992315930472dcf34c2f5d3fedf2f3db43627ce5/manifests/install.yaml

## install argocd

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/master/manifests/install.yaml

get password:

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

port-forward:

kubectl port-forward svc/argocd-server -n argocd 8080:443
