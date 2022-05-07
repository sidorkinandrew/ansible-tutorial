# Ansible tutorial: Grouping hosts

Hosts can be grouped -

```ini
[ubuntu]
host0
host1
host2
```

Or even shorter

```ini
[ubuntu]
host[0:2]
```

Child groups can be created via `[groupname:children]` syntax - 

```ini
[ubuntu]
host0

[centos]
host[1:2]

[linux:children]
ubuntu
centos
```


## Setting variables

With `ansible` or `ansible-playbook` command, variables can also be set
with `--extra-vars` (or `-e`) as `key=val` pairs 

Use `ansible_port` to modify the SSH port for a host - 

```ini
[ubuntu]
host0 ansible_host=192.168.0.12 ansible_port=2222
```

Ansible checks for variables in directories `group_vars` and `host_vars`

In our case `host0` variables will be searched in those files - 

- `group_vars/linux`  # linux - is the parent groupname
- `group_vars/ubuntu` # ubuntu - is the groupname
- `host_vars/host0`   # host_vars - variables for hosts files


Done? proceed to [step-04](../step-04/)