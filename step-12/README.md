# Ansible tutorial: Using tags

## Leveraging tags

Tags will let us select which part of the playbook we want to run.

Now we can ask Ansible to execute tasks by using `-t` parameter -

```bash
ansible-playbook pbook.yml -t interesting
```

Additionally, this is how we can `include` other yamls - 

```yaml
- include: haproxy.yml
```
