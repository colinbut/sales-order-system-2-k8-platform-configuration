# Customer - MySQL Deployment

## Create Secret

```bash
kubectl create secret generic mysql-secret --from-literal=mysql.root.password=password
```

As a later exercise, can put the secrets in a secure storage such as [AWS SSM Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html) or [Vault](https://www.vaultproject.io/)

## Apply ReplicaSet

```bash
kubectl apply -f mysql_rs.yml
```

## Apply Service

```bash
kubectl apply -f mysql_svc.yml
```