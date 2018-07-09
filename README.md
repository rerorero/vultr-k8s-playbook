# vultr-k8s-playbook
Ansible playbook to create vultr VMs and deploy a kubernetes cluster.

## Setup

Setup vultr API key.
```
vi ~/.vultr.ini
```
```
[default]
key=<Your vultr's API key>
```

Generate RSA key pair and register the public key via [vultr](https://my.vultr.com/sshkeys/).
```
ssh-keygen -f ./vultr.key
vi inventories # set your key id to vultr_key
```

You can modify `inventories` file to customize VMs.

## Playbooks

`site.yml` creates new VM instances and deploy a kubernetes cluster.
```
vi inventories # Modify VM props
ansible-playbook site.yml
```

`destroy.yml` deletes VMs.
```
ansible-playbook destroy.yml
```
Specify `-l deploy` if you want to remove only deploy server.
```
ansible-playbook destroy.yml -l deploy
```
