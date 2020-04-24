# Order Service Deployment

## Create ConfigMap

```bash
kubectl apply -f orderservice_configmap.yml
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