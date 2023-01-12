## 视频

https://www.bilibili.com/video/BV1Wv4y1y7Kr/?spm_id_from=333.999.0.0

## PPT

https://yunify.anybox.qingcloud.com/s/AzhJG9gefoqvzWfJNCBXhRgMGyPfl1k9

## 创建集群

```
kind create cluster --config kind/config.yaml
```

## 安装 ingress-nginx

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

## 安装 argocd

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/master/manifests/install.yaml
```

get password:

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

access argocd:

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

username: admin, password: get from above command

## 基础用法（Application CRD）

```
kubectl apply -f helm/application.yaml
```

## 多环境（代码即环境）

```
kubectl apply -f helm-env/applicationset.yaml
```

## 监听 PR 创建新环境（PR 即环境）

```
kubectl apply -f pr
```
