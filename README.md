# Wordpress 

## Deploy

`kubectl apply -f .`

## Delete all

`kubectl delete -f .`

## See if everything is OK

`kubectl -n production get pods`
```
NAME                      READY   STATUS    RESTARTS   AGE
mysql-0                   1/1     Running   0          4m13s
nginx-7774d9465f-4vbrh    1/1     Running   0          4m14s
phpfpm-566ccf66cf-mjkr9   1/1     Running   0          4m14s
```

`kubectl -n production get svc`
```
NAME     TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
mysql    ClusterIP   10.101.227.23    <none>        3306/TCP       90s
nginx    NodePort    10.101.103.69    <none>        80:30036/TCP   90s
phpfpm   ClusterIP   10.105.152.147   <none>        9000/TCP       90s
```

`kubectl -n production get pvc`
```
NAME                 STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
mysql-data-mysql-0   Bound    pvc-8bbdc51a-8845-11e9-96bb-0800275415f7   10Gi       RWO            standard       2m18s
wordpress-files      Bound    pvc-8b989cd9-8845-11e9-96bb-0800275415f7   1Gi        RWX            standard       2m19s
```

`kubectl -n production get secrets`
```
NAME                  TYPE                                  DATA   AGE
default-token-tqz64   kubernetes.io/service-account-token   3      68s
mysql-secrets         Opaque                                3      68s
phpfpm-secrets        Opaque                                2      68s
```

## Connect to Wordpress

`http://IP:30036`