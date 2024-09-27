Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

***srvr1c_add_repository***  
***srvr1c_add_repository_keyserver***  
***srvr1c_add_repository_id***  

***srvr1c_service_name***  
***srvr1c_full_service_name***  
***srvr1c_ras_service_name***  
***srvr1c_full_ras_service_name***  

***srvr1c_version***  
***srvr1c_destination***  
***srvr1c_services_destionation***  
***srvr1c_artifactory_directory***  
***srvr1c_run_files***  
***srvr1c_setup_run_file***  

***srvr1c_rac_user***  
***srvr1c_rac_group***  
***srvr1c_rac_port***  
 
***srvr1c_sentinel_fullnes_archive_file_name***  
***srvr1c_sentinel_pkg_archive_file_name***  
***srvr1c_sentinel_tmp_dir***  
***srvr1c_sentinel_fullnes_archive_dir***  
***srvr1c_sentinel_pkg_archive_dir***  

***srvr1c_aksusbd_service***   
***srvr1c_hasp_service***  
 
***srvr1c_default_locale***  
***srvr1c_locales_files***  
  **locale_gen**  
  **locale_conf**  
***srvr1c_locales***  
***srvr1c_locale_path***  

***srvr1c_shell_check_rac_service_status***  
***srvr1c_shell_rac_add_admin***  
***srvr1c_shell_rac_get_admin_info***  
***srvr1c_shell_rac_get_infobase***  
***srvr1c_shell_rac_drop_db***  
***srvr1c_shell_rac_create_db***  
***srvr1c_shell_rac_check_db_list***  
***srvr1c_shell_rac_get_general_cluster_info***  
***srvr1c_shell_rac_start_cluster***  

***srvr1c_shell_check_timezone***  
***srvr1c_shell_check_service_status***  
***srvr1c_shell_check_hold_package***  
***srvr1c_shell_install_1c***  
***srvr1c_shell_fix_broken_package***  
***srvr1c_shell_set_timezone***  
***srvr1c_shell_create_server_simlink***  
***srvr1c_shell_create_ras_simlink***  

***srvr1c_shell_postgresql_conf_postgresql_path***  
***srvr1c_shell_postgresql_conf_pg_hba_path***  
***srvr1c_shell_check_postgresql_status*** 

***srvr1c_shell_install_sentinel***  
***srvr1c_shell_check_aksusbd_status***  
***srvr1c_shell_check_hasplmd_status***  

***srvr1c_shell_check_apache2_status***  

***srvr1c_templates_service***  
***srvr1c_templates_ras_service***  

***srvr1c_cluster_admin_login***  
***srvr1c_cluster_admin_pass***  
***srvr1c_cluster_database_type***  

***srvr1c_postgresql_locale***  
***srvr1c_postgresql_license_distribution***  
***srvr1c_postgresql_scheduled_jobs***  
***srvr1c_postgresql_db_descr***  
***srvr1c_postgresql_db_name***  
***srvr1c_postgresql_user***  
***srvr1c_postgresql_group***  
***srvr1c_postgresql_psql_pass***  
***srvr1c_postgresql_package_name***  
***srvr1c_postgresql_service***  
***srvr1c_postgresql_conf_dir***  
***srvr1c_postgresql_conf_file***  
***srvr1c_postgresql_repo_url***  
***srvr1c_postgresql_repo_dest***  
***srvr1c_postgresql_service***  
***srvr1c_postgresql_conf_dir***  
***srvr1c_postgresql_conf_file***  
***srvr1c_templates_postgresql_conf_file***  
***srvr1c_postgresql_subnet***  

***srvr1c_apache_service***  
***srvr1c_apache_webservice_name***  
***srvr1c_apache_vrd_dir***  
***srvr1c_apache_conf_file***  
***srvr1c_apache_publish_webinst***  

***srvr1c_test_version***  
***srvr1c_test_destination***  
***srvr1c_test_run_files***  
***srvr1c_test_setup_run_file***  
***srvr1c_test_shell_install_1c***  
***srvr1c_test_service_name***  
***srvr1c_test_full_service_name***  
***srvr1c_test_serice_port***  
***srvr1c_test_database_name***  
***srvr1c_test_service_user***  
***srvr1c_test_templates_service***  
***srvr1c_test_shell_check_service_status***  

***srvr1c_debug_status***  

***srv1c_hosts***  

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

***Start role***  
**Раскатка prod контура**  
ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml  

**Раскатка test контура**  
ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml --extra-vars "srvr1c_traning_use=true"  

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
