Ansible Role: Hamlet
=========

Deploys and configures a Django app to a shared hosting server running nginx and postgres.

Requirements
------------

TBD

Role Variables
--------------

Required:
- `app_name`  
_The name of the app._  
Used in:
    - folder in shared sites directory: _/srv/sites/{{ app_name }}_
    - name of the gunicorn service: _/etc/systemd/system/{{ app\_name}}.service_
    - name of the nginx config: _/etc/nginx/sites-available/{{ app\_name }}.service_

- `branch_name`
asdf

- `git_repo`  
asdf

Optional:
- `sites_dir`  
_The directory all sites are stored in._  
Default: `/srv/sites`  

- `app_dir`  
_The directory the app is stored in._  
Default: `"{{ sites_dir + '/' + app_name }}"`  

- `project_name`  
_The name of the project created with `django-admin startproject`. Used to locate `wsgi.py`._  
Default: `"{{ app_name }}"`


Dependencies
------------

None.

Example Playbook
----------------

Pending

License
-------

[MIT](LICENSE)