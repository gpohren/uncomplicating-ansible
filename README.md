# Uncomplicating Ansible

Project for Kubernetes cluster installation using Ansible and AWS

## Create EC2 instances

Execute in provisioning

```bash
ansible-playbook -i hosts main.yml
```

Public IP addresses and private IP addresses generated on the hosts (provisioning)

```bash
[kubernetes]
172.31.24.64
172.31.26.171
172.31.30.240
52.58.176.7
3.121.98.248
54.93.106.9
```

## Install Kubernetes

Insert IP addresses generated on hosts (install_k8s)

```bash
[k8s-master]
52.58.176.7

[k8s-workers]
3.121.98.248
54.93.106.9

[k8s-workers:vars]
K8S_MASTER_NODE_IP=172.31.24.64
K8S_API_SECURE_PORT=6443
```

Execute in install_k8s

```bash
ansible-playbook -i hosts main.yml
```
