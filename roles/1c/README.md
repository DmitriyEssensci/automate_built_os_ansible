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
***srvr1c_ras_service_name***  

***srvr1c_version***  
***srvr1c_destination***  
***srvr1c_services_destionation***  
***srvr1c_artifactory_directory***  
***srvr1c_run_files***  
***srvr1c_setup_run_file***  
 
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

***srvr1c_postgresql_user***  
***srvr1c_postgresql_group***  
***srvr1c_postgresql_psql_pass***  

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
ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml  

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
