# Customer Service Deployment

## Create ConfigMap

```bash
CUSTOMER_SERVICE_PROPERTIES=https://github.com/colinbut/sales-order-system-2-k8-platform-configuration/blob/master/live/dev/customer/customerservice.properties
kubectl create configmap customerservice-configmap \ 
--from-file=${CUSTOMER_SERVICE_PROPERTIES} \
--from-literal=spring.datasource.url="jdbc:mysql://customer-service-mysql/customerdb?createDatabaseIfNotExist=true&autoReconnect=true&useSSL=false&allowPublicKeyRetrieval=true"

```

## Create Secret

```bash
kubectl create secret generic customerservice-secret \
--from-literal=spring.datasource.username=[] \
--from-literal=spring.datasource.username=[] \
--from-literal=jwt.secret=[]
```

## Apply Deployment

```bash
```

## Apply Service

```bash
```