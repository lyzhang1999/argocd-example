## create cluster

1. kind create cluster --config kind/config.yaml

## install ingress-nginx

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

## install argocd

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

get password:

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

port-forward:

kubectl port-forward svc/argocd-server -n argocd 8080:443 --address='0.0.0.0'
