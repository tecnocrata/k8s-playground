In order to get various resources, we can use:

```
kubectl get deployment,pods
```

## Edit deployment directly

```
kubectl edit deploy hello-php
```

## Via kubectl

```
kubectl scale deploy hello-php --replicas=3
```
