# Home Assistant deployed on Kubernetes @ home

- [k8s@home](https://github.com/k8s-at-home)
- [MicroK8s](https://microk8s.io/)

## Setup

### Server

#### Ubuntu Server

1. Flash RPi to boot from USB (Available in Rpi imager)
2. Install Ubuntu Server 21.10 on SSD
3. Boot Ubuntu from SSD and upgrade software `sudo apt update && sudo apt upgrade -y && sudo snap refresh`

##### Zerotier

- Install zerotier

##### Mkcert.dev

- Install mkcert.dev (`/usr/local/bin/mkcert-v1.4.3-linux-arm64`) + CA

#### MicroK8s

```sh
sudo snap install microk8s --classic
```

```sh
microk8s enable dns storage helm3
sudo snap alias microk8s.kubectl kubectl
sudo snap alias microk8s.kubectl k
sudo snap alias microk8s.helm3 helm3
sudo snap alias microk8s.helm3 helm
```

##### Portainer

```sh
microk8s enable portainer
```

### Home Assistant

#### Helm Chart

```sh
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm install home-assistant k8s-at-home/home-assistant -f ./charts/home-assistant/values.yaml
```

> **Modifications to values.yaml**: HA version, Timezone, enabled hostNetwork, enabled config persistence


## TODO

- [ ] (portainer) ingress and reverse proxy (+ local)
- [ ] ingress and reverse proxy (+ local)
- [ ] ingress and reverse proxy (+ external)
- [ ] OpenEBS for storage
- [ ] Backup persisted PVCs (config, movies, downloads, scans, etc.) (external disk?)
- [ ] Prometheus + Grafana to monitor status and metrics (HA, MicroK8s, etc)
- [ ] GitOps --> Helm Charts --> to reality
- [ ] 



