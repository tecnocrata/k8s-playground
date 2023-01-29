Exposing the hello-php app within a container and within a pod under a deployment

```
kubectl expose deployment/hello-php --port 80 --type=NodePort
```
