ansible-amazon
==============

Utils for Amazon, currently contains the script for stop/start &amp; bucket lifecycles.

A virtual env for Ansible2 is installed because it is required while the playbooks are pushed via template if their required variables are specified.

Role Variables
--------------

**virtual_env_path**

   Path for the ansible virtual env installation

   default: ``"/home/admin/"``

**utils_path**

   Path to which scripts will be installed - reuse that for crons

   default: ``"/home/admin/aws-utils"``

**utils_user**

   User for the utils directory

   default: ``"admin"``

**utils_group**

   Group for the utils directory

   default: ``"admin"``

**start_stop_list**

   If defined, make the start-stop script pushed into utils directory
   e.g.:
```
   start_stop_list:
     - {project: 'my_project1', role: 'admin', env: 'dev'}
     - {project: 'my_project1', role: 'memcached', env: 'dev'}
     - {project: 'my_project2', role: 'front', env: 'preprod'}
     - {project: 'my_project3', role: 'memcached', env: 'preprod'}
     - {project: 'my_project3', role: 'front', env: 'dev'}
```

   default: ``undefined``

**lifecycle_policies**

   If defined, make the 'backup lifecycle' script pushed into utils directory
   e.g.:
```
   lifecycle_policies:
     - bucket: my_bucket1
       name: my_unique_policy_name1
       transition_days: 60
       expiration_days: 365
       prefix: my_bucket1/dir1/dir2/
     - bucket: my_bucket2
       name: my_unique_policy_name2
       name: my_bucket2
       transition_days: 7
       expiration_days: 30
       prefix: my_bucket2/dir1/dir2/
     - bucket: warnerbros-backup
       name: my_unique_policy_name3
       transition_days: 180
       expiration_days: 730
       prefix: my_bucket2/dir1/dir3/
```

   default: ``undefined``

License
-------

MIT

Author Information
------------------

Hugo Rosnet at Cycloid.io
