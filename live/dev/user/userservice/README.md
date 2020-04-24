# User Service Deployment

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