Whith the following instructions we are going to create a ClusterIP service

Using a generator

```
kubectl apply -f hello-php-pod.yaml
#generator
kubectl expose pod/hello-php-for-service --dry-run=client --port 80 -o yaml > service.generated.yaml
kubectl apply -f service.generated.yaml
```

Creating directly the service

```
kubectl apply -f hello-php-pod.yaml
kubectl expose pod/hello-php-for-service --port 80 -o yaml
```
