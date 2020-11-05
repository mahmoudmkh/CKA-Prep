# CKA-Prep
## install auto-completion
yum install install bash-completion
echo "source <(kubectl completion bash)" >> ~/.bashrc
source .bashrc.


## Tips and Triks

working version 1.14

kubectl create deployment nginx-deploy --image=nginx:1.18.0-alpine --dry-run=client -o yaml > nginx-deploy.yaml 

working version 1.14

kubectl run --generator=run-pod/v1 elephant --image=redis --dry-run -o yaml > elaphant.yaml

not working version 1.14

kubectl run busybox1.19 --image=busybox --restart=Never --dry-run=client -o yaml > busybox1.19.yaml 

-----------------------------------update version-------------------------------------------------

cat <<EOF > /etc/yum.repos.d/kubernetes.repo
  
[kubernetes]
name=Kubernetes

baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64

enabled=1

gpgcheck=1

repo_gpgcheck=1

gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg

EOF
yum install -y kubectl

yum install -y kubeadm-v1.19.0-0 --disableexcludes=kubernetes

yum install -y kubectl-v1.19.0-0 --disableexcludes=kubernetes

systemctl daemon-reload

-----------------------------------------------------------------------------------------------------

working on version 1.19

kubectl run busybox1.19 --image=busybox --restart=Never --dry-run=client -o yaml > busybox1.19.yaml 

working on version 1.19

kubectl create deployment nginx-deploy --image=nginx:1.18.0-alpine --dry-run=client -o yaml > nginx-deploy.yaml

not working on version 1.19

kubectl run --generator=run-pod/v1 elephant --image=redis --dry-run -o yaml > elaphant.yaml

yum list --showduplicates kubeadm --disableexcludes=kubernetes
journalctl -u kubelet


------------------------------------------------------------
sudo kubeadm reset 
sudo yum remove kubeadm kubectl kubelet kubernetes-cni kube*    
sudo yum autoremove 
sudo rm -rf ~/.kube
---------------------------
yaml generator
------------------------------
https://k8syaml.com/

---------------------------
information about token
------------------------------
# https://jwt.io/

metric and monitoring
-----------------------------
mkdir monitoring ; cd monitoring

git clone https://github.com/kodekloudhub/kubernetes-metrics-server.git

cd kubernetes-metrics-server/

kubectl create -f . 

# => pod added on the system namespace kube-system   metrics-server-774b56d589-4t6vg

controlplane $ kubectl top node

NAME           CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%

controlplane   155m         7%     995Mi           52%

node01         1997m        99%    488Mi           12%

controlplane $ kubectl top pod

NAME       CPU(cores)   MEMORY(bytes)

elephant   13m          50Mi

lion       959m         1Mi

rabbit     977m         1Mi
