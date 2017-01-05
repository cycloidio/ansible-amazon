ansible-amazon
==============

Utils for Amazon, currently contains the script for stop/start &amp; bucket lifecycles.

Role Variables
--------------

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

 **start_stop_rds_list**

    If defined, make the start-stop script to resize RDS instances pushed into utils directory
    e.g.:
 ```
    start_stop_rds_list:
      - instance_name: foo
        region: eu-west-1
        stopped:
          instance_type: db.t2.micro
        running:
          instance_type: db.t2.small
 ```

    default (`instance_type` and `instance_name` are required):

 ```
     rds_defaults:
       wait_timeout: 600
       region: eu-west-1
       stopped:
         instance_type: db.t2.micro
 ```

**lifecycle_policies**

   If defined, make apply lifecycle policy on s3 bucket.
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
     - bucket: backup
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
