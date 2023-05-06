# Configmaps mounted in volume

Every key in the configmap will be a separated file

Create the configmap

```sh
kubectl create configmap nginx-conf --from-file nginx.conf --from-file hello.md
```
