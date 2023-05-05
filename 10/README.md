# Configmaps

For exposing a pod directly we can do this

```
kubectl port-forward hello-php 8000:80
```

## Simple pod with env variables hardcoded

`pod-with-env.yaml`

## Simple pod refering values from configmap

`pod-with-configmap1.yaml`
