# Infrastructure

## How to start a new VM

- Buy a VM on some hosting
  - When ordering add user `ansible` with ssh public key, if possible
- Add to `inventory/common.yaml`
  - If w/o user ansible, add `provided_user`, `provided_pass`
- Run ansible playbooks

## Installation

```shell
poetry install
# show env
poetry show env
# activate env
$(poetry env activate)
```

## Playbooks

### Postgresql VM

Run playbooks one by one:
- normalize.yaml:   Ssh keys, sudo.
- ddns.yaml:        Dynamic dns client.
- postgresql.yaml:  Run postgresql, import .dump files into DBs.

```shell
cd deploy/ansible

# Sudo, authorized_keys, sshd_config (port, ...)
ansible-playbook normalize.yaml -e ansible_port=22 -l cat-vm1
# DDNS
ansible-playbook ddns.yaml -l cat-vm1
# OpenVPN configuration
ansible-playbook postgresql.yaml -l cat-vm1
```

