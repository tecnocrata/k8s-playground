```
{
apt install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt update && apt install -y docker-ce=5:19.03.10~3-0~ubuntu-focal containerd.io
}
```

```
cat <<EOF > /etc/docker/daemon.json
{
    "insecure-registries" : [ "192.168.56.1:5000" ]
}
EOF
```
In the host machine run:

```
docker run -d -p 5000:5000 --restart always --name registry registry:2
```

## Setting up Rancher

Start rancher at node0 using:

```
docker run --privileged -d --restart=unless-stopped -v /opt/rancher:/var/lib/rancher -p 8080:80 -p 443:443 rancher/rancher
```

Remember to disable ingress

Add nodes using

```
sudo docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run  rancher/rancher-agent:v2.7.0 --server https://192.168.56.211 --token kjzfgpl7zqb64cfgdpgxqxz2bpwg2ggfxcfbdr2d7wzt2846vm77l2 --ca-checksum a15be2d5ada7618b487e6c214ae3f9edd5acb03221b2ab84565c69a2d4f23184 --address 192.168.56.212 --internal-address 192.168.56.212 --etcd --controlplane --worker

sudo docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run  rancher/rancher-agent:v2.7.0 --server https://192.168.56.211 --token kjzfgpl7zqb64cfgdpgxqxz2bpwg2ggfxcfbdr2d7wzt2846vm77l2 --ca-checksum a15be2d5ada7618b487e6c214ae3f9edd5acb03221b2ab84565c69a2d4f23184 --address 192.168.56.213 --internal-address 192.168.56.213 --etcd --controlplane --worker
```

## Configure kubectl at host machine

Download the config file and place it into `~/.kube/config`

Execute the following commands for testing:

```
kubectl get pods
kubectl run nginx --image=nginx:latest
kubectl get pods -w
```