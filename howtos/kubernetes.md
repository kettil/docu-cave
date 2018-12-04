# Install Kubernetes



## Init

- disable swap

```bash
# user: root
apt-get update
apt-get upgrade -y
apt-get install -y nano sudo git

usermod -aG sudo kettil
```

## Docker

```bash
# user: root
apt-get install -y apt-transport-https ca-certificates curl gnupg2 software-properties-common

curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -

apt-key fingerprint 0EBFCD88
# pub   rsa4096 2017-02-22 [SCEA]
#       9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
# uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
# sub   rsa4096 2017-02-22 [S]

echo "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list

apt-get update

# list of all version
#apt-cache madison docker-ce

# installed last version
#apt-get install -y docker-ce
apt-get install -y docker-ce=18.06.1~ce~3-0~debian

groupadd docker
usermod -aG docker kettil
```

Source:
- https://docs.docker.com/install/linux/docker-ce/debian/
- https://docs.docker.com/install/linux/linux-postinstall/

## Kubernetes

```bash
# user: root
apt-get install -y apt-transport-https curl

curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

apt-key fingerprint BA07F4FB
# pub   rsa2048 2018-04-01 [SCEA] [expires: 2021-03-31]
#       54A6 47F9 048D 5688 D7DA  2ABE 6A03 0B21 BA07 F4FB
# uid           [ unknown] Google Cloud Packages Automatic Signing Key <gc-team@google.com>

echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" > /etc/apt/sources.list.d/kubernetes.list

apt-get update
apt-get install -y kubelet kubeadm kubectl
apt-mark hold kubelet kubeadm kubectl
# see https://manpages.debian.org/stretch/apt/apt-mark.8.en.html

kubeadm config images pull
kubeadm init --pod-network-cidr=10.y.0.0/16 --apiserver-advertise-address=10.x.x.x
# example: kubeadm init --pod-network-cidr=10.10.0.0/16 --apiserver-advertise-address=10.0.0.10
# 10.10.0.0/16 => 10.10.0.1 - 10.10.255.254
```

### User settings

```bash
# user: kettil
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

kubectl version
# Client Version: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"<hash>", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
# Server Version: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"<hash>", GitTreeState:"clean", BuildDate:"2018-10-24T06:43:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}

# for single machine (master only)
kubectl taint nodes --all node-role.kubernetes.io/master-
# node/<hostname> untainted

```

Source:
- https://kubernetes.io/docs/setup/independent/install-kubeadm/
- https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/

### Network

```bash
# user: kettil
sudo sysctl net.bridge.bridge-nf-call-iptables=1
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

# test config
kubectl get pods --namespace=kube-system | grep flannel
> kube-flannel-ds-amd64-bzdp5         1/1     Running   0          74s
```

Source:
- https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/

### Dashboard

```bash
# user: root
apt-get install easy-rsa
cd /usr/share/easy-rsa/
source ./vars
./clean-all
./build-ca
./build-key dashboard

mkdir -p /home/kettil/certs
cp keys/dashboard.crt keys/dashboard.key /home/kettil/certs/
chown -R kettil:kettil /home/kettil/certs

# ----------
# user: kettil
kubectl create secret generic kubernetes-dashboard-certs --from-file=$HOME/certs -n kube-system
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml


nano db-permissions.yaml
# apiVersion: rbac.authorization.k8s.io/v1beta1
# kind: ClusterRoleBinding
# metadata:
#   name: kubernetes-dashboard
#   labels:
#     k8s-app: kubernetes-dashboard
# roleRef:
#   apiGroup: rbac.authorization.k8s.io
#   kind: ClusterRole
#   name: cluster-admin
# subjects:
# - kind: ServiceAccount
#   name: kubernetes-dashboard
#   namespace: kube-system

kubectl create -f db-permissions.yaml

nohup kubectl proxy --address=0.0.0.0 --disable-filter=true &
```

> http://10.x.x.x:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/

Source:
- https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/
- https://github.com/kubernetes/dashboard/wiki/Installation
- https://www.edureka.co/blog/install-kubernetes-on-ubuntu/amp/

## Helm

```bash
# user: kettil
cd ~
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > install-helm.sh
chmod 700 install-helm.sh
./install-helm.sh

kubectl -n kube-system create serviceaccount tiller
kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller

helm init --service-account tiller
# for upgrade
#helm init --upgrade

# test
kubectl get pods --namespace kube-system
> tiller-deploy-845cffcd48-rp7vl          1/1     Running            0          19m

helm repo update

```

Source:
- https://www.digitalocean.com/community/tutorials/how-to-install-software-on-kubernetes-clusters-with-the-helm-package-manager
- https://docs.helm.sh/using_helm/#installing-helm

### Gitlab

```bash

helm repo add gitlab https://charts.gitlab.io/
helm repo update
helm upgrade --install gitlab gitlab/gitlab \
  --timeout 600 \
  --set global.hosts.domain=example.com \
  --set global.hosts.externalIP=10.x.x.x \
  --set certmanager-issuer.email=email@example.com  \
  --set gitlab.migrations.image.repository=registry.gitlab.com/gitlab-org/build/cng/gitlab-rails-ce \
  --set gitlab.sidekiq.image.repository=registry.gitlab.com/gitlab-org/build/cng/gitlab-sidekiq-ce  \
  --set gitlab.unicorn.image.repository=registry.gitlab.com/gitlab-org/build/cng/gitlab-unicorn-ce  \
  --set gitlab.unicorn.workhorse.image=registry.gitlab.com/gitlab-org/build/cng/gitlab-workhorse-ce \
  --set gitlab.task-runner.image.repository=registry.gitlab.com/gitlab-org/build/cng/gitlab-task-runner-ce
```

Source:
- https://docs.gitlab.com/ee/install/kubernetes/gitlab_chart.html
