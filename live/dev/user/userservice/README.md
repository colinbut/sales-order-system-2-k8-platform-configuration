# User Service Deployment


## Create ConfigMap

```bash
curl -O https://raw.githubusercontent.com/colinbut/sales-order-system-2-k8-platform-configuration/master/live/dev/user/userservice.yml && \
kubectl create configmap userservice-config --from-file=userservice.yml
```

## Create Secrets

```bash
kubectl create secret generic userservice-secret \
--from-literal=spring.datasource.username=admin \
--from-literal=spring.datasource.password=password \
--from-literal=jwt.secret=userservice
```

## Apply Deployment

```bash
kubectl apply -f userservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f userservice_svc.yml
```