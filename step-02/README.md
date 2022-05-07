# Ansible tutorial: Talking to nodes

## Shell module

This module lets you execute a shell command on the remote host -

```bash
ansible -i step-02/hosts -m shell -a 'uname -a' host0
```

## Copy module

```bash
ansible -i step-02/hosts -m copy -a 'src=/etc/hosts dest=/tmp/' host0
```

[Ansible module list](http://docs.ansible.com/list_of_all_modules.html)

Get release information on Ubuntu versions deployed on hosts -

```bash
ansible -i step-02/hosts -m shell -a 'grep DISTRIB_RELEASE /etc/lsb-release' all
```

## Setup module

Module `setup` specializes in hosts' _facts_ gathering.

```bash
ansible -i step-02/hosts -m setup host0
```

How much memory are on all your hosts - 

```bash
ansible -i step-02/hosts -m setup -a 'filter=ansible_memtotal_mb' all
```

## Selecting hosts

[Other ways to select hosts](http://docs.ansible.com/intro_patterns.html) - 

- `host0:host1` would run on host0 and host1
- `host*` would run on all hosts starting with 'host' and ending with ''

Done? proceed to [step-03](./step-03/README.md)