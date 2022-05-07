# Ansible tutorial: Variables again

## Fine tuning our HAProxy configuration

Let's use variables to configure weights and check interval.

## Group vars

The check interval will be set in a group_vars file for haproxy.

The file `group_vars/haproxy.yml` - it has to be named after the group
you want to define the variables for.

```yaml
haproxy:
    check_interval: 3000
    stats_socket: /tmp/sock
```

## Hosts vars

Hosts vars live in files under `host_vars` directory and the variables
defined in `host_vars` files overrides variables from `group_vars`.

## Updating the template

The template must be updated to use these variables.

Please note that using `haproxy_stats_sockets=/tmp/sock"` is highly insecure!

Now, run the playbook - 

```bash
ansible-playbook -i step-10/hosts step-10/haproxy.yml
```

The updated haproxy playbook looks like this - 

```yaml
- hosts: web
  gather_facts: true
......
```

We've added an empty play for `web` hosts at the top to trigger facts gathering.
This is required because if the haproxy playbook is started without apache's,
otherwise ansible will complain that `ansible_all_ipv4_addresses` key doesn't exist.

Use this quick bash one-liner to generate some load - 
```bash
for i in {0..100}; do curl 192.168.33.10; done
```


Done? proceed to [step-11](./step-11/README.md)