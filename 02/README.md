#

Execute for generating a pod definition

```
kubectl run hello-php --image=tecnocrata/hello-php:2.1 --restart=Never --port=80 --dry-run -o yaml
```
