# Product Service Deployment

## Create ConfigMap

```bash
kubectl apply -f productservice_configmap.yml
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