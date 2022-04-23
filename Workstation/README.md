# Workstation Setup
Workstation setup for Ubuntu like distros. Tested only on Kubuntu 21.10.

## How to

Install dependencies: Git and Ansible
```bash
sudo apt update
sudo apt install git ansible --no-install-recommends
```

Clone this repo
```bash
git clone https://github.com/Maurifc/Ansible-Playground.git
```

Get into playbook folder
```bash
cd Ansible-Playground/Workstation
```

Run playbook
```bash
ansible-playbook playbook.yaml --ask-become-pass
```
## To Do
**Improvements**
- Add check if helm is installed before download it
- Add check if terraform is installed before download it
- Standardize names (PROGRAM - ACTION)
- Skip clones if folder already exists
- Get aliases and pet config from backup

**Create install task:**
 - NVM

