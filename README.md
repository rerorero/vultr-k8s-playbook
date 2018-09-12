# vultr-k8s-playbook
Ansible playbook to create vultr VMs and deploy a kubernetes cluster.

## Setup

Create a `.vultr.ini` file in your home directory to pass the API Key.
```
vi ~/.vultr.ini
```
```
[default]
key=<Your API key>
```

Generate RSA key pair and register the public key via [vultr](https://my.vultr.com/sshkeys/).
```
ssh-keygen -f ./vultr.key
vi inventories # set your key id to vultr_key
```

You can modify `inventories` file to customize VMs.

## Playbooks

`site.yml` creates new VM instances and deploy a kubernetes cluster by running kubespray.
```
vi inventories # Modify VM props
ansible-playbook site.yml
```

`destroy.yml` deletes VMs.
```
ansible-playbook destroy.yml
```
With `-l deploy` option it removes only deploy servers.
```
ansible-playbook destroy.yml -l deploy
```

`copy-kubeconf-to-local.yml` copies a kubeconf file from the master node to your local machine. Pass `dest` variable to specify the destination file path.
```
ansible-playbook copy-kubeconf-to-local.yml -e "dest=~/.kube/config.vultr"
```
