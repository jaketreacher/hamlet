Ansible Role: Hamlet
=========

Deploys and configures a Django app to a shared hosting server running nginx and postgres.

Requirements
------------

TBD

Role Variables
--------------

`sites_dir: /srv/sites`  
The directory all sites are stored in.

`app_name: ''`  
The name of the app.

`app_dir: "{{ sites_dir + '/' + app_name }}"`  
The directory the app is stored in.

Dependencies
------------

None.

Example Playbook
----------------

Pending

License
-------

[MIT](LICENSE)