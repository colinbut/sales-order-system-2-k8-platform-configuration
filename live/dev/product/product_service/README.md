# Product Service Deployment

## Create ConfigMap

```bash
curl -O https://raw.githubusercontent.com/colinbut/sales-order-system-2-k8-platform-configuration/master/live/dev/product/productservice.properties
kubectl create configmap productservice-config --from-file=productservice.properties
```

## Create Secret

```bash
kubectl create secret generic productservice-secret \
--from-literal=jwt.secret=userservice
```

## Apply Deployment

```bash
kubectl apply -f productservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f productservice_svc.yml
```