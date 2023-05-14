# Secrets

This folder contains all the possible ways to use secrets

There are 3 different ways to test them:

```bash
k apply -f pod-with-secrets1.yaml
kubectl exec -it hello-php -- /bin/bash
env
```

```bash
k apply -f pod-with-secrets2.yaml
kubectl exec -it hello-php -- /bin/bash
env
```

```bash
kubectl exec -it hello-php -- ls /tmp
kubectl exec -it hello-php -- cat /tmp/password
```
