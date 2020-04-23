# Order Service Deployment

## Create ConfigMap

```bash
kubectl create configmap orderservice-configmap \
--from-file=https://github.com/colinbut/sales-order-system-2-k8-platform-configuration/blob/master/live/dev/order/orderservice.properties
```

## Create Secret

```bash
kubectl create secret generic orderservice-secret \
--from-literal=jwt.secret=[]
```

## Apply Deployment

```bash
kubectl apply -f orderservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f orderservice_svc.yml
```