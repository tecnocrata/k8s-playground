Whith the following instructions we are going to create a ClusterIP service

First of all, we need to create a pod, it is not tied to the service

```bash
kubectl apply -f hello-php-pod.yaml
kubectl get pods
```

We are going to create a service based on that pod (already running)

```bash
#generator
kubectl expose pod/hello-php-for-service --dry-run=client --port 80 -o yaml > service.generated.yaml
kubectl apply -f service.clusterip.generated.yaml
```

Creating directly the service

```
kubectl apply -f hello-php-pod.yaml
kubectl expose pod/hello-php-for-service --port 80 -o yaml
```

Verificar que se pueda comunicar hacia los pods detras del ClusterIP service desde otro pod

Usando un comando como para correr una imagen pero dentro del cluster de kubernetes, parecido a docker run

```
kubectl run --rm -i --tty my-small-linux --image alpine --restart=Never -- sh
```

Dentro del contenedor dentro del pod, ejecutamos y obtenemos resultados similares para los dos siguientes comandos:

```
wget hello-php-for-service/index.php -qSO-
wget hello-php-for-service -qSO-
```

# NodePort

Ahora analizamos el servicio de tipo Nodeport

```
kubectl expose pod/hello-php-for-service --dry-run=client --type=NodePort --port 80 -o yaml > service.nodeport.generated.yaml
```
