# Ansible tutorial: setup

## Starting up Vagrant VMs

`vagrant up`

## Adding your SSH keys on the virtual machines

```bash
ansible-playbook -i step-00/hosts step-00/setup.yml
```

## [SECURITY] Disabling SSH host check

Uncomment the 
#host_key_checking = False
in the /etc/ansible/ansible.cfg

```bash
cat /etc/ansible/ansible.cfg  | grep host_key_checking
# host_key_checking = False
```

Done? proceed to [step-01](../step-01/)