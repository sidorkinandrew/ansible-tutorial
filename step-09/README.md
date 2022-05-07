# Ansible tutorial: templates


## Adding HAProxy as loadbalancer

Jinja2 template can use variables - 
`{{ inventory_hostname }}` or `{{ ansible_default_ipv4.address}}`
and it also support conditionals, for-loops, etc...

Adding `templates/haproxy.cfg.j2` for the HAProxy config file
with values of the addresses/names of the `web` servers.

## HAProxy playbook

We must run both Apache and HAProxy playbooks at same time, 
since the haproxy playbook requires facts _from_ the two webservers.

```bash
$ ansible-playbook -i step-09/hosts step-09/apache.yml step-09/haproxy.yml
```

Visit [http://192.168.33.10/](http://192.168.33.10/) to see the result.

You can also peek at HAProxy's statistics at
[http://192.168.33.10/haproxy?stats](http://192.168.33.10/haproxy?stats).


Done? proceed to [step-10](./step-10/README.md)