

```
cat <<EOF > /etc/docker/daemon.json
{
    "insecure-registries" : [ "192.168.56.1:5000" ]
}
EOF
```

```
sudo docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run  rancher/rancher-agent:v2.7.0 --server https://192.168.56.211 --token kjzfgpl7zqb64cfgdpgxqxz2bpwg2ggfxcfbdr2d7wzt2846vm77l2 --ca-checksum a15be2d5ada7618b487e6c214ae3f9edd5acb03221b2ab84565c69a2d4f23184 --address 192.168.56.212 --internal-address 192.168.56.212 --etcd --controlplane --worker

sudo docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run  rancher/rancher-agent:v2.7.0 --server https://192.168.56.211 --token kjzfgpl7zqb64cfgdpgxqxz2bpwg2ggfxcfbdr2d7wzt2846vm77l2 --ca-checksum a15be2d5ada7618b487e6c214ae3f9edd5acb03221b2ab84565c69a2d4f23184 --address 192.168.56.213 --internal-address 192.168.56.213 --etcd --controlplane --worker
```