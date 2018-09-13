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
_A single variables for simple configuration_  
If this is not specified, the following three will be required:  
app_dir, project_name, file_name  

- `git_repo`  
_The path of the git repo to fetch_

- `branch_name`
_The name of the branch to fetch from the `git_repo`_
Used in:
    - fetching the git branch
    - to construct a unique `file_name`

- `server_name`  
_The name of the server in the nginx config_

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

- `file_name`  
_The name of various files_  
Default: `"{{ app_name + '.' + branch_name }}"`  


Dependencies
------------

None.

Example Playbook
----------------

Pending

License
-------

[MIT](LICENSE)