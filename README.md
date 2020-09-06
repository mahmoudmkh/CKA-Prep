# CKA-Prep
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
yum install -y kubectl-1.19.0 --disableexcludes=kubernetes
systemctl daemon-reload
-----------------------------------------------------------------------------------------------------

working on version 1.19
kubectl run busybox1.19 --image=busybox --restart=Never --dry-run=client -o yaml > busybox1.19.yaml 
working on version 1.19
kubectl create deployment nginx-deploy --image=nginx:1.18.0-alpine --dry-run=client -o yaml > nginx-deploy.yaml
not working on version 1.19
kubectl run --generator=run-pod/v1 elephant --image=redis --dry-run -o yaml > elaphant.yaml
