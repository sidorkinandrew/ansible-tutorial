# Ansible tutorial: Migrating to roles

Roles are a new way of organizing files in Ansible with some interesting
features. More on the features here - [Ansible's documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html).
Roles also can have interdependencies: role B can depend on another role A.

## Roles structures

Roles assume a specific file organization thus helping building modular playbooks
and much simpler housekeeping.

The `main.yml` files wille be added to the play automatically.

The actual data (e.g. variables) shoul d be outside of roles and play.
This way, roles can be shared easily, without exposing sensitive data.

You can set defaults for variables in roles (to ensure your roles always work)
in the `defaults` directory.

The `meta` directory used to add dependencies.

## Creating the Apache role

Create the following structure for apache role:

```bash
mkdir -p step-11/roles/apache/{tasks,handlers,files}
```

Move `tasks` into the the `tasks` folder as `main.yml`;
extract and move the `handlers` part into the appropriate folder;
move `files/` and `templates/` into the relevant roles accordingly.

## Create a role playbook

Let's create a top level playbook `site.yml` - 

```yaml
- hosts: web
  roles:
    - apache

- hosts: haproxy
  roles:
    - haproxy
```

To proceed with moving haproxy files for this role,
we can use `ansible-galaxy` to create the required structure - 

```bash
ansible-galaxy --offline init step-11/roles/haproxy
```

## Apply the roles

We can try out our new playbook with - 

```bash
ansible-playbook -i step-11/hosts step-11/site.yml
```

In case we need tun just one role, use the `limit` flag-

```bash
ansible-playbook -i step-11/hosts -l web step-11/site.yml
```


Done? proceed to [step-12](../step-12/)