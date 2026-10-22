# ansible-proxmox

Ansible playbook for the first setup of Proxmox

<img width="500" height="699" alt="the lord of the rings" src="https://github.com/user-attachments/assets/c5874864-0c7b-4ec2-b97e-3d158daebfde" />

### Usage

```bash
ansible-galaxy collection install -r requirements.yml
cp inventory/hosts.ini.example inventory/hosts.ini
cp group_vars/all.yml.example group_vars/all.yml
ansible-playbook proxmox.yml
```

### Add Terraform user and role

Run on the Proxmox host:

```bash
pveum user add terraform@pve
pveum role add Terraform -privs "Datastore.AllocateSpace,Datastore.AllocateTemplate,Datastore.Audit,SDN.Audit,SDN.Use,Sys.Audit,Sys.Modify,VM.Allocate,VM.Audit,VM.Config.CDROM,VM.Config.CPU,VM.Config.Cloudinit,VM.Config.Disk,VM.Config.HWType,VM.Config.Memory,VM.Config.Network,VM.Config.Options,VM.GuestAgent.Audit,VM.PowerMgmt"
pveum acl modify / --users terraform@pve --roles Terraform
pveum user token add terraform@pve provider --privsep 0
```

Put the token into `credentials.auto.tfvars` in terraform-proxmox as `terraform@pve!provider=<value>`
