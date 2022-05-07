# Ansible tutorial: Restarting when config is correct

## Check Apache config before restarting

Adding an "apache2ctl configtest" check for the configuration correctness - 

```yaml
...
    - name: Check that our config is valid
      become: yes
      command: apache2ctl configtest
...
```

Let's run the playbook - 

```bash
$ ansible-playbook -i step-06/hosts step-06/apache.yml
```
