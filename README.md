# Ansible-Playground
Just some tests with Ansible's playbooks

## Docker Portainer
Provision a machine with Docker and Portainer. 

Plus, it...: 
 - Updates SOs packages
 - Creates SysAdmin user
 - Sets up iptables firewall 

## Workstation
Provision a basic Workstation with:
- Docker, VirtualBox, Vagrant, Minikube, etc...
- Aliases
- Some fixes

## Basic Commands
```bash
ansible-playbook playbook.yaml --ask-become-pass
```