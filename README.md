# homeservers

## Setup

Setup vultr API key.
```
vi ~/.vultr.ini
```
```
[default]
key=<Your vultr's API key>
```

Generate key pair and register them via [vultr](https://my.vultr.com/sshkeys/).
```
ssh-keygen -f ./vultr.key
vi group_vars/all.yml # set your key id to vultr_key
```

## Playbooks

Provision
```
vi inventories # Modify VM props
ansible-playbook site.yml
```

Destroy
```
ansible-playbook destroy.yml
```
