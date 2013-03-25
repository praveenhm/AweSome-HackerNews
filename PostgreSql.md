#### steps to install and work with the PostgreSql 8.4.11



### localhost posgtgresql 8.4.11 external, not the embedded_db comes with the CDH4
           yum install pgadmin3    # install the admin tool
           subl /var/lib/pgsql/data/postgresql.conf 
           subl /var/lib/pgsql/data/pg_hba.conf
           service postgresql status
           service postgresql stop
           service postgresql start
           chkconfig postgresql on   
           sudo -u postgres psql   
           
           
           $ sudo -u postgres psql
           could not change directory to "/home/praveen"
           psql (8.4.13)
           Type "help" for help.
           
           postgres=# select name, setting from pg_settings where category = 'File Locations';
                  name        |               setting               
           -------------------+-------------------------------------
            config_file       | /var/lib/pgsql/data/postgresql.conf
            data_directory    | /var/lib/pgsql/data
            external_pid_file | 
            hba_file          | /var/lib/pgsql/data/pg_hba.conf
            ident_file        | /var/lib/pgsql/data/pg_ident.conf
           (5 rows)
           
           postgres=# SELECT name, context, setting, boot_val, reset_val FROM pg_settings WHERE name in('listen_addresses','max_connections','shared_buffers','effective_cache_size','work_mem', 'maintenance_work_mem') ORDER BY context,name;
           
                    name         |  context   | setting | boot_val  | reset_val 
           ----------------------+------------+---------+-----------+-----------
            listen_addresses     | postmaster | *       | localhost | *
            max_connections      | postmaster | 100     | 100       | 100
            shared_buffers       | postmaster | 4096    | 1024      | 4096
            effective_cache_size | user       | 16384   | 16384     | 16384
            maintenance_work_mem | user       | 16384   | 16384     | 16384
            work_mem             | user       | 1024    | 1024      | 1024
           (6 rows)
          


          
