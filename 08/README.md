Exposing the hello-php app within a container and within a pod under a deployment

```
kubectl expose deployment/hello-php --port 80 --type=NodePort
```

The deployment.yaml contains a docker image reference updated, and update the deployment and service using

```bash
k apply -f deployment.yaml
```
