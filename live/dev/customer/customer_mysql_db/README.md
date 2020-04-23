# Customer - MySQL Deployment

## Create Secret
```bash
kubectl create secret generic mysql-secret --from-literal=mysql.root.password=password
```

## Apply ReplicaSet

```bash
kubectl apply -f mysql_rs.yml
```

## Apply Service

```bash
kubectl apply -f mysql_svc.yml
```