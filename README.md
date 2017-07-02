# minikube-startup-china
a quick guide for how to run minikube in china because the great firewall of China 
这篇文章的安装只针对macOS

## 安装minikube

- 首先到VisualBox的官方网站安装VisualBox的最新版本
- 到minikube Github官方网站（https://github.com/kubernetes/minikube）上参考安装minikube
  `brew cask install minikube`

- 安装kubectl
  `brew install kubectl`
  
## 启动minikube

`minikube start --registry-mirror=http://44d249ac.m.daocloud.io`

## 进入虚拟机手动拉取镜像，并运行docker tag

`minikube ssh` 然后进入到命令模式，依次执行下面的命令：

```
docker pull dockermonster/pause-amd64:3.0
docker tag dockermonster/pause-amd64:3.0 gcr.io/google_containers/pause-amd64:3.0

docker pull dockermonster/kube-addon-manager:v6.4-beta.1
docker tag dockermonster/kube-addon-manager:v6.4-beta.1 gcr.io/google-containers/kube-addon-manager:v6.4-beta.1

docker pull dockermonster/echoserver:1.4
docker tag dockermonster/echoserver:1.4 gcr.io/google_containers/echoserver:1.4

docker pull dockermonster/kubernetes-dashboard-amd64:v1.6.1
docker tag dockermonster/kubernetes-dashboard-amd64:v1.6.1 gcr.io/google_containers/kubernetes-dashboard-amd64:v1.6.1

docker pull dockermonster/k8s-dns-kube-dns-amd64:1.14.2
docker tag dockermonster/k8s-dns-kube-dns-amd64:1.14.2 gcr.io/google_containers/k8s-dns-kube-dns-amd64:1.14.2

docker pull dockermonster/k8s-dns-dnsmasq-nanny-amd64:1.14.2
docker tag dockermonster/k8s-dns-dnsmasq-nanny-amd64:1.14.2 gcr.io/google_containers/k8s-dns-dnsmasq-nanny-amd64:1.14.2

docker pull dockermonster/k8s-dns-sidecar-amd64:1.14.2
docker tag dockermonster/k8s-dns-sidecar-amd64:1.14.2 gcr.io/google_containers/k8s-dns-sidecar-amd64:1.14.2


docker pull dockermonster/defaultbackend:1.0
docker tag dockermonster/defaultbackend:1.0 gcr.io/google_containers/defaultbackend:1.0

docker pull dockermonster/heapster:v1.3.0
docker tag dockermonster/heapster:v1.3.0 gcr.io/google_containers/heapster:v1.3.0

docker pull dockermonster/heapster_grafana:v2.6.0-2
docker tag dockermonster/heapster_grafana:v2.6.0-2 gcr.io/google_containers/heapster_grafana:v2.6.0-2

docker pull dockermonster/heapster_influxdb:v0.6
docker tag dockermonster/heapster_influxdb:v0.6 gcr.io/google_containers/heapster_influxdb:v0.6

docker pull dockermonster/nginx-ingress-controller:0.9.0-beta.4
docker tag dockermonster/nginx-ingress-controller:0.9.0-beta.4 gcr.io/google_containers/nginx-ingress-controller:0.9.0-beta.4
```

## 退出minikube命令模式

直接输入`exit`

## kubectl启动echoserver 镜像并生成pod

`kubectl run hello-minikube --image=dockermonster/echoserver:1.4 --port=8080`

## 查看pod运行情况

`kubectl get pods`

## 查看kubenetes面板

`kubectl dashboard`

## 关闭minikube

`minikube stop`






