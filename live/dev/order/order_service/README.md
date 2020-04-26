# Order Service Deployment

## Create ConfigMap

```bash
kubectl apply -f orderservice_configmap.yml
```

## Create Secret

```bash
kubectl create secret generic orderservice-secret --from-literal=jwt.secret=userservice
```


As a later exercise, can put the secrets in a secure storage such as [AWS SSM Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html) or [Vault](https://www.vaultproject.io/)

## Apply Deployment

```bash
kubectl apply -f orderservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f orderservice_svc.yml
```