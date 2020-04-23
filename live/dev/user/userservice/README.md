# User Service Deployment


## Create ConfigMap

```bash
kubectl create configmap userservice-configmap --from-file=https://github.com/colinbut/sales-order-system-2-k8-platform-configuration/blob/master/live/dev/user/userservice.yml
```

## Create Secrets

```bash
kubectl create secret generic userservice-secret \
--from-literal=spring.datasource.username=[db username] \
--from-literal=spring.datasource.password=[db password] \
--from-literal=jwt.secret=[the jwt secret to use]
```

## Apply Deployment

```bash
kubectl apply -f userservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f userservice_svc.yml
```