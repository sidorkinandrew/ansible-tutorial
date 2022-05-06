# Ansible tutorial: Inventory

The default place for inventory - a file is  `/etc/ansible/hosts`.
[configurable via environment variable `ANSIBLE_INVENTORY`, or the `-i` flag.

`ansible_host` is a special _variable_ that sets the IP ansible will use when
trying to connect to this host. 

`ansible_user` is another special _variable_ that tells ansible to
connect as this user when using ssh. By default ansible would use your
current username, or use another default provided in ~/.ansible.cfg
(`remote_user`).

## Testing

Let's run ad-hoc module command - 

```bash
ansible -m ping all -i step-01/hosts
```

