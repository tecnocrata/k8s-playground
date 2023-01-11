Executing the containter

```
docker run --rm -it -p 8000:80 hello-php
```

Executing under kubernetes:

```
kubectl run hello-node --image=tecnocrata/hello-php:2.1 --port=80
```
