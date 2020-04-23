# Product Service Deployment

## Create ConfigMap

```bash
kubectl create configmap productservice-configmap \
--from-file=https://github.com/colinbut/sales-order-system-2-k8-platform-configuration/blob/master/live/dev/product/productservice.properties
```

## Create Secret

```bash
kubectl create secret generic productservice-secret --from-literal=jwt.secret=[]
```

## Apply Deployment

```bash
kubectl apply -f productservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f productservice_svc.yml
```