# Ansible tutorial: Using conditionals

## Reverting when things go wrong

Rewriting our playbook to continue processing even if 
there is a failure but we also need to revert what's done.

The `files/my-new-awesome-app` config contains a typo in the line #2- 

```ini
...
  RocumentDoot /var/www/my-new-awesome-app
...
```

after running the playbook -

```bash
$ ansible-playbook -i step-07/hosts -l host1 step-07/apache.yml
```

We'll see that it fails - this is expected and we also print a message.

By editing the `files/my-new-awesome-app` config line back to - 

```ini
...
  DocumentRoot /var/www/my-new-awesome-app
...
```

the scripts proceeds as usual, skipping the steps tagged with the `when` conditional.

The `register` keyword records output from a command (exit status, stdout, stderr, ...), 
and `when: result is failed` checks if the registered variable (`result`) contains a failed status.

Done? proceed to [step-08](./step-08/README.md)