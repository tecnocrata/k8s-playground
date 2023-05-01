## Installing an ingress-controllebr based on nginx:

```bash
helm upgrade --install ingress-nginx ingress-nginx \
--repo https://kubernetes.github.io/ingress-nginx \
--namespace ingress-nginx --create-namespace
```

Verify the ingress is running

```
k get pods -n ingress-nginx
```

Edit /etc/hosts files to use a unreal domain, adding the next line:

```
192.168.60.211  tecnocrata-k8s.com
```

## Using the ingress

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
