Ansible Role: Hamlet
=========

Deploys and configures a Django app to a shared hosting server running nginx and postgres.

Requirements
------------

- psycopg2 (if postgres used)

Role Variables
--------------

The variables are contained in a dictionary as the encapsulation makes it easier to manage. The structure is below:

```
hamlet:
    project:
        dir
        name
    git:
        repo
        branch
    db:
      name
      user
      pass
    daemon_name
    server_name
```

Parameter | Comments
:---: | ---
project.dir | The directory the project should be placed in.
project.name | The name of the project created with `django-admin startproject`. Used to locate `wsgi.py`.
git.repo | The git repo.
git.branch | The branch to fetch. Will also be used to make a unique nginx file name, <br/>`{{ hamlet.project.name + '-' + hamlet.git.branch }}.conf`
db.name | Database name
db.user | Database user
db.pass | Database password
daemon_name | The name of the gunicorn daemon service that will be serving the website
server_name | The address nginx should listen on.

<br/>
Flags for Letsencrypt are kept outside of the dictionary to enable defaults to be set.  

Parameter | Default | Comments
:---: | --- |---
letsencrypt_enabled | False | Whether to use HTTPS
letsencrypt_domains | | A list of domains to be passed into Certbot. Required if `letsencrypt_enabled` is True.
letsencrypt_staging | False | Use the staging server to obtain test certificates.

Dependencies
------------

None.

Example Playbook
----------------

```
roles:
  - {
      role: hamlet,
      hamlet: {
        project: {
          dir: "/srv/sites/hamlet_demoapp",
          name: "hamlet_test"
        },
        git: {
          repo: "https://github.com/jaketreacher/hamlet_demoapp.git",
          branch: production
        },
        db: {
          name: hamlet-prod,
          user: hamlet,
          pass: password
        },
        daemon_name: hamlet_test.prod,
        server_name: hamlet-test
      }
```

License
-------

[MIT](LICENSE)


