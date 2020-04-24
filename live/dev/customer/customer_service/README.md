# Customer Service Deployment

## Create ConfigMap

```bash
kubectl apply -f customerservice_configmap.yml
```

## Create Secret

```bash
kubectl create secret generic customerservice-secret \
--from-literal=spring.datasource.username=[] \
--from-literal=spring.datasource.password=[] \
--from-literal=jwt.secret=[]
```

## Apply Deployment

```bash
kubectl apply -f customerservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f customerservice_svc.yml
```