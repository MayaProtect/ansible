# Ansible

## Prepare hosts file

```ini
[master]
192.168.1.27

[nodes]
192.168.1.28
192.168.1.29
192.168.1.31

[cluster:children]
master
nodes
```

- `[master]` section is for k3s server node
- `[nodes]` section is for k3s agents node

## Apply Update

`ansible-playbook 01_update_all.yml -i ./inventory/hosts.ini`

## Install k3s

`ansible-playbook 02_k3s_install.yml -i ./inventory/hosts.ini`

### Configure kubectl

`scp k3suser@<ip_master>:~/.kube/config ~/.kube/config`

## Reset k3s

`ansible-playbook 99_k3s_reset.yml -i ./inventory/hosts.ini`
