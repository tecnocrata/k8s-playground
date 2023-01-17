Many ways to install a k8s cluster

1. Using Rancher (RKE): https://www.youtube.com/watch?v=ZbSFG4cSYhk
   - Steps and scripts: https://kamrul.dev/deploy-multi-node-kubernetes-cluster-locally-with-rancher/
2. Using Vagrant scripts (no RKE, plain K8s installation): https://github.com/justmeandopensource/kubernetes/tree/master/vagrant-provisioning
   - Using Rancher as container will solve my problems????: https://www.youtube.com/watch?v=jF5L6IgZ5To
3. Using microk8s: https://www.youtube.com/watch?v=GPVH9fHW0Dk
   - It seems simple and light in resources
   - However depends on `microk8s` command all the time
4. Using k3s: https://www.youtube.com/watch?v=UdjhFLV1yt8&t=443s

Setup Rancher independently

Ensure docker has been installed

Rancher documentation here: https://www.rancher.com/quick-start

```sh
$ sudo docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 -v /opt/rancher:/var/lib/rancher rancher/rancher
```
