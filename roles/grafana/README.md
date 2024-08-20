Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

***grafana_ensure_keyrings***  

***grafana_download_pgp***  

***grafana_repo***   

***grafana_convert_gpg***  

***grafana_dest_gpg***  

***grafana_check_version***  

***grafana_service_status***  

***grafana_config_file***  

***grafana_dashboard_path***  

***grafana_dashboard_main_dashboard_name*** 

***grafana_dashboard_main_dashboard_dir***  

***grafana_host_address***  

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
ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/install_apps.yml

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
