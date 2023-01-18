```
docker build -t hello-php:error .
docker tag hello-php:error tecnocrata/hello-php:error
docker push tecnocrata/hello-php:error
```

### Liveness Probe

- Se usa para saber si el contenedor esta 'vivo'
- Es el clasico o tipico health check
- Si el livenessProbe retorna un error kubernetes reiniciara el contenedor y por ende el pod
- Intentara un numero de veces verificar que el health check responda correctamente
- Luego de esos intentos, reiniciara el contenedor
- Luego, intentara reiniciar (varias veces configurable) el contenedor, si luego de un numero de intentos no se puede levantar el contenedor sin obtener un error en el health check, kubernetes marcara el contenedor como 'con error' y no lo volvera a reiniciar.
- Los [[timeout]]y el numero de reintentos es configurable (mas adelante)
- En resumen si este health check falla se reinicia el contenedor y/o el pod

### Readiness Probe

- Se usa para saber si la aplicacion/contenedor esta lista para recibir peticiones/trafico
- Si el contenedor no devuelve una respuesta correcta el [[pod]] no se agrega al service, esto es lo mismo que el pod no acepte trafico
- Si el contenedor estaba funcionando bien, por ende el pod tambien, pero de repente el readinessProbe empieza a devolver errores, kubernetes quitara el pod del objeto services (y especificamente de su [[loadbalancer]])
- Lo anterior es lo mismo que decir que no recibira trafico.
- En resumen: si este health check falla el pod NO recibe trafico
- [[k8s]] sacara al [[pod]] del objeto service donde este, hasta que el readiness responda correctamente
