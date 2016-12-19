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

License
-------

MIT

Author Information
------------------

Hugo Rosnet at Cycloid.io
