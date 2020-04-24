# Order Service Deployment

## Create ConfigMap

```bash
curl -O https://raw.githubusercontent.com/colinbut/sales-order-system-2-k8-platform-configuration/master/live/dev/order/orderservice.properties
kubectl create configmap orderservice-config --from-file=orderservice.properties
```

## Create Secret

```bash
kubectl create secret generic orderservice-secret --from-literal=jwt.secret=[]
```

## Apply Deployment

```bash
kubectl apply -f orderservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f orderservice_svc.yml
```