Testing
=======

Running Tests
-------------
Steps to run tests:
```
$ pwd
> hamlet
$ cd tests
$ vagrant up
$ ansible-playbook test.yml
$ vagrant destroy -f # cleanup
```

The following result signifies that all tests have passed:  
`localhost : ok=5 changed=0 unreachable=0 failed=0`
<hr>

Further Details
---------------
Vagrant will create a single VM which will hosts two sites - production and staging.  
`test.yml` will configure everything _and_ run tests to ensure the website is displaying the correct information.  

Test | Significance
--- | ---
Check Branch | The git repo has been fetched, and the correct branch is showing
Check DB Engine | The .env files has been copied and read, and the database credentials are correct
Check DB Name | Same as above. Redundant.  
Image | Static files have been configured correctly in nginx.  
_any_ | Nginx has been configured properly