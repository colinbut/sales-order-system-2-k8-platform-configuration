# Product Redis Data Store - Deployment


## Create ConfigMap

```bash
kubectl create configmap \
--from-file=slave.conf=./conf/slave.conf \
--from-file=master.conf=./conf/master.conf \
--from-file=sentinel.conf=./conf/sentinel.conf \
--from-file=init.sh=./etc/init.sh \
--from-file=sentinel.sh=./etc/sentinel.sh \
redis-config
```

## Apply StatefulSet

```bash
kubectl apply -f redis_sts.yml
```

## Apply Service

```bash
kubectl apply -f redis_svc.yml
```