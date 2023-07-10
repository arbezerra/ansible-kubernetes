# Kubernetes Cluster

Deploy a Production Kubernetes Cluster with Ansible.

- Kubeadm
- Cilium
- Metrics Server
- Metallb
- Ingress Nginx
- Rocky Linux 9

## Prerequisites

- Master has a external and internal network interfaces, and workers have only internal interface.
- Configure `/etc/hosts` in all nodes
- Passwordless ssh login in all nodes (with jumphost if necessary)
- Firewall must allow all trafic for the internal network
- Nodes must masquerade and forward traffic

## Install

1. Change `--apiserver-advertise-address` to the external ip of master in `playbooks/cluster.yml`, and change the load balancer ip pool on `playbooks/metallb.yml`, and change both staging and production emails in `playbooks/cert-manager.yml`.

2. Set the hostnames of nodes in the file `hosts`.

3. Execute the ansible playbook with `ansible-playbook -i hosts install.yml`.