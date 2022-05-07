# Ansible tutorial: Deploying our website from git

## The git module

Adding installation `libapache2-mod-php` and `git` package
(used to clone some sample application's git repository).

The deployment from `github.com` could look like this - 

```yaml
....
    - name: Deploy our awesome application
      git:
        repo: https://github.com/leucos/ansible-tuto-demosite.git
        dest: /var/www/awesome-app
      tags: deploy
....
```

To run the playbok - 

```bash
$ ansible-playbook -i step-08/hosts step-08/apache.yml
```

You can now curl/lynx/browse to [http://192.168.33.11](http://192.168.33.11)

Note: the `tags: deploy` allows for direct executing only this part of the playbook.

```bash
$ ansible-playbook -i step-08/hosts step-08/apache.yml -t deploy
```

Done? proceed to [step-09](../step-09/)