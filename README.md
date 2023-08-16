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

1. Copy `defaults/main.yml` to `values.yml` and change the values.

2. Set the hostnames of nodes in the file `hosts`.

3. Execute the ansible playbook with `ansible-playbook -i hosts site.yml --ask-become-pass --extra-vars="@values.yml"`.