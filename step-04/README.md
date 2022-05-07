# Ansible tutorial: Ansible playbooks

## Install Apache 

Update the hosts inventory file - 

```ini
[web]
host0 ansible_host=192.168.33.10
host1 ansible_host=192.168.33.11
host2 ansible_host=192.168.33.12
```

We're using the [apt](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html) module to install debian packages.

```yaml
- hosts: web
  tasks:
    - name: Installs apache web server
      become: yes
      apt:
        pkg: apache2
        state: present
        update_cache: true
```

You can run the playbook (lets call it `apache.yml`):

```bash
ansible-playbook -i step-04/hosts step-04/apache.yml
```

Done? proceed to [step-05](./step-05/README.md)