## create cluster

1. kind create cluster --config kind/config.yaml

## install argocd

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
