# ansible-proxmox

Ansible playbook for the first setup of Proxmox

### Usage

```bash
ansible-galaxy collection install -r requirements.yml
cp inventory/hosts.ini.example inventory/hosts.ini
cp group_vars/all.yml.example group_vars/all.yml
ansible-playbook proxmox.yml
```
