Using a generator:

```
kubectl create deployment hello-php --image tecnocrata/hello-php:2.1 --dry-run=client -o yaml --port=80 > deployment.yaml
kubectl apply -f deployment.yaml
```
