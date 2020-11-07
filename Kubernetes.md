# Hello World
centos 8
install:
```console
[tveld@localhost ~]$ sudo yum remove buildah skopeo podman
[tveld@localhost ~]$ sudo yum install -y yum-utils
[tveld@localhost ~]$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
[tveld@localhost ~]$ sudo yum install docker-ce docker-ce-cli containerd.io
[tveld@localhost ~]$ cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
exclude=kubelet kubeadm kubectl
EOF
[tveld@localhost ~]$ sudo setenforce 0
[tveld@localhost ~]$ sudo sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config
[tveld@localhost ~]$ sudo yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes
[tveld@localhost ~]$ sudo systemctl enable --now kubelet
```
