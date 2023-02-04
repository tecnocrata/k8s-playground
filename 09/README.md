We can use a generator to create an ingress object, this way:

```sh
kubectl create ingress test --rule=mydemo.com/serv1=s1:80 --rule=mydemo.com/serv2=s2:80 --dry-run=client -o yaml
```

for this example we will use this other one:

```sh
kubectl create ingress hello-world --rule=tecnocrata-k8s.com/=hello-php:80 --dry-run=client -o yaml > ingress.yaml
```

this will create the `ingress.yaml` file

It is not required that the ingress name matches with service or pod names

```sh
kubectl apply -f ingress.yaml
```
