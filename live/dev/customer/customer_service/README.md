# Customer Service Deployment

## Create ConfigMap

```bash
kubectl apply -f customerservice_configmap.yml
```

## Create Secret

```bash
kubectl create secret generic customerservice-secret \
--from-literal=spring.datasource.username=root \
--from-literal=spring.datasource.password=password \
--from-literal=jwt.secret=secret
```

As a later exercise, can put the secrets in a secure storage such as [AWS SSM Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html) or [Vault](https://www.vaultproject.io/)

## Apply Deployment

```bash
kubectl apply -f customerservice_deploy.yml
```

## Apply Service

```bash
kubectl apply -f customerservice_svc.yml
```