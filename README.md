# Uncomplicating Ansible

Project for Kubernetes cluster installation using Ansible and AWS

[LINUXtips - Uncomplicating Ansible](https://www.linuxtips.io/product-page/descomplicando-o-ansible)

## Create EC2 instances

Adjust variables

```bash
$ cat provisioning/roles/creating-instances/vars/main.yml
---
# vars file for creating-instances
instance_type: t2.medium
sec_group_name: giropops
image: ami-00ddb0e5626798373
keypair: ansible-class
region: us-east-1
count: 3
profile: giropops
```

Execute in provisioning

```bash
ansible-playbook -i hosts main.yml
```

Public IP addresses and private IP addresses generated on the hosts

```bash
$ cat provisioning/hosts
[kubernetes]
172.31.24.64
172.31.26.171
172.31.30.240
52.58.176.7
3.121.98.248
54.93.106.9
```

## Install Kubernetes

Insert IP addresses generated on hosts

```bash
$ cat install_k8s/hosts
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
