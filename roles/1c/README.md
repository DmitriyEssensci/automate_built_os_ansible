Role Name
=========
Данная роль позволяет установить 1с со всеми зависимыми сервисами. Настраивается тонкий, толстый и веб клиент, устанавливается postgresql, apache2, hasp, а так же создаётся "тестовый" контур, который устанавливает тестовую конфигурацию 1с.

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

***srvr1c_traning_use***  
Переменная объявлена в default/main.yml, содержит в себе пустое значение для того чтобы запускатьплейбук с екстра параметром true/ false.

***srvr1c_service_name***  
Переменная объявлена в default/main.yml, содержит в себе краткое название сервиса 1с, используется в 
***srvr1c_full_service_name***  
Переменная объявлена в default/main.yml, содержит в себе полное название сервиса 1с, используется в 
***srvr1c_ras_service_name***  
Переменная объявлена в default/main.yml, содержит в себе краткое название сервиса rac, используется в 
***srvr1c_full_ras_service_name***  
Переменная объявлена в default/main.yml, содержит в себе полное название сервиса rac, используется в 

***srvr1c_version***  
Переменная объявлена в default/main.yml, содержит в себе версию пакета 1с для установки, используется в 
***srvr1c_destination***  
Переменная объявлена в default/main.yml, содержит в себе директорию куда будет ставиться 1с на сервере, используется в 
***srvr1c_services_destionation***  
Переменная объявлена в default/main.yml, содержит в себе директорию куда будут ставиться сервисы 1с на сервере, используется в 
***srvr1c_artifactory_directory***  
Переменная объявлена в default/main.yml, содержит в себе название папки-хранилища в котором лежат все пакеты для установки, используется в 
***srvr1c_run_files***  
Переменная объявлена в default/main.yml, содержит в себе название архива где лежит .run файл пакета 1с, используется в 
***srvr1c_setup_run_file***  
Переменная объявлена в default/main.yml, содержит в себе название установочного пакета 1с, используется в 

***srvr1c_rac_sys_dir***  
Переменная объявлена в default/main.yml, содержит в себе системную директорию для сервиса rac, используется в 
***srvr1c_rac_user***  
Переменная объявлена в default/main.yml, содержит в себе название пользователя для rac, используется в 
***srvr1c_rac_group***  
Переменная объявлена в default/main.yml, содержит в себе название группы для rac, используется в 
***srvr1c_rac_port***  
Переменная объявлена в default/main.yml, содержит в себе номер порта для сервиса rac, используется в 
 
***srvr1c_sentinel_fullnes_archive_file_name***  
Переменная объявлена в default/main.yml, содержит в себе название архива где лежат пакеты для установки сервисов hasp и aksusbd, используется в 
***srvr1c_sentinel_pkg_archive_file_name***  
Переменная объявлена в default/main.yml, содержит в себе название директории где лежат установочные пакеты для aksusbd, используется в 
***srvr1c_sentinel_tmp_dir***  
Переменная объявлена в default/main.yml, содержит в себе название директории с пакетами sentinel, используется в 
***srvr1c_sentinel_fullnes_archive_dir***  
Переменная объявлена в default/main.yml, содержит в себе название директории куда перемещаются разархированные пакеты sentinel, используется в 
***srvr1c_sentinel_pkg_archive_dir***  
Переменная объявлена в default/main.yml, содержит в себе название директории куда перемещаются разархированные пакеты sentinel для сервиса aksusbd, используется в 

***srvr1c_aksusbd_service***   
Переменная объявлена в default/main.yml, содержит в себе полное название сервиса aksusbd, используется в 
***srvr1c_hasp_service***  
Переменная объявлена в default/main.yml, содержит в себе полное название сервиса hasplmd, используется в 
 
***srvr1c_default_locale***  
Переменная объявлена в default/main.yml, содержит в себе название локалей которые будут ставиться поумолчанию, используется в 
***srvr1c_locales_files***  
Переменная объявлена в default/main.yml, содержит в себе переменные для пработы с локали, используется в 
  **locale_gen**  
  Переменная объявлена в default/main.yml, содержит в себе название директории до генерационного локали файла, используется в 
  **locale_conf**  
  Переменная объявлена в default/main.yml, содержит в себе название директории до конфигурационного файла локалей, используется в 
***srvr1c_locales***  
Переменная объявлена в default/main.yml, содержит в себе название локалей, которые будут выставлены, используется в 
***srvr1c_locale_path***  
Переменная объявлена в default/main.yml, содержит в себе путь к исполняемому сервису отвечающему за локали, используется в 

***srvr1c_shell_check_rac_service_status***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проверяет статус rac сервиса, используется в 
***srvr1c_shell_rac_add_admin***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая устанавливает админа поумолчанию с его учётными данными в rac сервер, используется в 
***srvr1c_shell_rac_get_admin_info***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая выводит всю информацию об админах в rac, используется в 
***srvr1c_shell_rac_get_infobase***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая выводит всю информацию о бд, которые установлены в rac, используется в 
***srvr1c_shell_rac_drop_db***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая удаляет бд, используется в 
***srvr1c_shell_rac_create_db***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая создаёт бд, используется в 
***srvr1c_shell_rac_check_db_list***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая выводит всю информацию о базах данных в списке, используется в 
***srvr1c_shell_rac_get_general_cluster_info***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая выводит всю информацию по кластеру, используется в 
***srvr1c_shell_rac_start_cluster***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая запускает демон кластера, используется в 

***srvr1c_shell_check_timezone***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проверяет правильную таймзону, используется в 
***srvr1c_shell_check_service_status***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проверяет статус сервиса 1с, используется в 
***srvr1c_shell_install_1c***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая устанавливает 1с с ключами, используется в 
***srvr1c_shell_fix_broken_package***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая устраняет неисправности в связях после/ перед установкой пакетов, используется в 
***srvr1c_shell_set_timezone***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая устанавливает правильные таймзоны, используется в 
***srvr1c_shell_create_server_simlink***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проводит симлинки с сервисом 1с, используется в 
***srvr1c_shell_create_ras_simlink***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проводит симлинки с сервисом rac, используется в 

***srvr1c_shell_postgresql_conf_postgresql_path***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая запускается в оболочке psql и выполняет запрос на вывод конфигурационного файла - postgresql, используется в 
***srvr1c_shell_postgresql_conf_pg_hba_path***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая запускается в оболочке psql и выполняет запрос на вывод конфигурационного файла - pg_hba, используется в 
***srvr1c_shell_check_postgresql_status***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проверяет статус сервиса postgrespro-1c-14, используется в 

***srvr1c_shell_install_sentinel***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая устанавливает методами dpkg hasp сервисы, используется в 
***srvr1c_shell_check_aksusbd_status***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проверяет статус сервиса aksusbd, используется в 
***srvr1c_shell_check_hasplmd_status***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проверяет статус сервиса hasplmd, используется в 

***srvr1c_shell_check_apache2_status***  
Переменная объявлена в default/main.yml, содержит в себе команду, которая проверяет статус сервиса apache2, используется в 

***srvr1c_templates_service***  
Переменная объявлена в default/main.yml, содержит в себе директории для перемещения сервисных файлов связанных с сервисом 1с, используется в 
***srvr1c_templates_ras_service***  
Переменная объявлена в default/main.yml, содержит в себе директории для перемещения сервисных файлов связанных с сервисом rac, используется в 

***srvr1c_cluster_admin_login*** 
Переменная объявлена в default/main.yml, содержит в себе учётные данные в виде логина для админа кластера rac, используется в 
***srvr1c_cluster_admin_pass***  
Переменная объявлена в default/main.yml, содержит в себе учётные данные в виде пароля для админа кластера rac, используется в 
***srvr1c_cluster_database_type***  
Переменная объявлена в default/main.yml, содержит в себе тип базы данных для кластера rac, используется в 

***srvr1c_pgadmin_email***  
Переменная объявлена в default/main.yml, содержит в себе email для доступа к интерфейсу сервиса pgadmin4, используется в 
***srvr1c_pgadmin_pass***  
Переменная объявлена в default/main.yml, содержит в себе пароль для доступа к интерфейсу сервиса pgadmin4, используется в 

***srvr1c_postgresql_locale***  
Переменная объявлена в default/main.yml, содержит в себе локаль postgresql для установки в базу данных, используется в 
***srvr1c_postgresql_license_distribution***  
Переменная объявлена в default/main.yml, содержит в себе значение включения лицензионного соглашения, используется в 
***srvr1c_postgresql_scheduled_jobs***  
Переменная объявлена в default/main.yml, содержит в себе значение включения шедулера на джобу, используется в 
***srvr1c_postgresql_db_descr***  
Переменная объявлена в default/main.yml, содержит в себе значение в виде краткого описания для базы данных, используется в  
***srvr1c_postgresql_db_name***  
Переменная объявлена в default/main.yml, содержит в себе значение наименования базы данных, используется в 
***srvr1c_postgresql_user***  
Переменная объявлена в default/main.yml, содержит в себе логин юзера Postgresql, используется в 
***srvr1c_postgresql_group***  
Переменная объявлена в default/main.yml, содержит в себе группу юзера Postgresql, используется в 
***srvr1c_postgresql_psql_pass***  
Переменная объявлена в default/main.yml, содержит в себе пароль юзера Postgresql, используется в 
***srvr1c_postgresql_package_name***  
Переменная объявлена в default/main.yml, содержит в себе название пакета postgresql, который устанавливается, используется в 
***srvr1c_postgresql_addr***  
Переменная объявлена в default/main.yml, содержит в себе адресс postgresql на котором будут хоститься базы данных, используется в 
***srvr1c_postgresql_port***  
Переменная объявлена в default/main.yml, содержит в себе порт postgresql на котором будут хоститься базы данных, используется в 
***srvr1c_postgresql_service***  
Переменная объявлена в default/main.yml, содержит в себе название сервиса postgresql, используется в 
***srvr1c_postgresql_conf_dir***  
Переменная объявлена в default/main.yml, содержит в себе путь к директории с конфигурационными файлами для postgresql, используется в 
***srvr1c_postgresql_conf_file***  
Переменная объявлена в default/main.yml, содержит в себе конфигурационный файл для postgresql, используется в 
***srvr1c_postgresql_repo_url***  
Переменная объявлена в default/main.yml, содержит в себе репозиторий откуда скачиваются методанные для его установки в систему, используется в 
***srvr1c_postgresql_repo_dest***  
Переменная объявлена в default/main.yml, содержит в себе директорию куда будет прописываться репозиторий, используется в 
***srvr1c_templates_postgresql_conf_file***  
Переменная объявлена в default/main.yml, содержит в себе директории для перемещения конфигурационных файлов для сервиса postgresql, используется в 
***srvr1c_postgresql_addr_subnet***   
Переменная объявлена в default/main.yml, содержит в себе только маску подсети для проведения настроек сервиса postgresql, используется в 
***srvr1c_postgresql_subnet***  
Переменная объявлена в default/main.yml, содержит в себе сетевую настройку маски подсети для конфигурационного файла postgresql, используется в 

***srvr1c_apache_service***  
Переменная объявлена в default/main.yml, содержит в себе название сервиса apache2, используется в 
***srvr1c_apache_webservice_name***  
Переменная объявлена в default/main.yml, содержит в себе название веб сервиса 1с, который будет доступен по данном имени, используется в 
***srvr1c_apache_webservice_addr***  
Переменная объявлена в default/main.yml, содержит в себе адрес веб сервиса 1с и всех сервисов на котором apache2 будет поднимать сервисы, используется в 
***srvr1c_apache_vrd_dir***  
Переменная объявлена в default/main.yml, содержит в себе директорию с вебсервисом 1с, используется в 
***srvr1c_apache_conf_file***  
Переменная объявлена в default/main.yml, содержит в себе конфигурационный файл apache2, используется в 
***srvr1c_apache_publish_webinst***  
Переменная объявлена в default/main.yml, содержит в себе команду для запуска веб сервиса 1с на apache2 по веб клиенту 1с, используется в 

############# TEST #############
***srvr1c_test_version***  
Переменная объявлена в default/main.yml, содержит в себе версию 1с для тестовой конфигурации, используется в 
***srvr1c_test_destination***  
Переменная объявлена в default/main.yml, содержит в себе путь куда будет ставить тестовая конфигурация 1с, используется в 
***srvr1c_test_run_files***  
Переменная объявлена в default/main.yml, содержит в себе название архива для установки тестовой конфигурации 1с, используется в 
***srvr1c_test_setup_run_file***  
Переменная объявлена в default/main.yml, содержит в себе название .run файла для установки тестовой конфигурации 1с, используется в 
***srvr1c_test_shell_install_1c***  
Переменная объявлена в default/main.yml, содержит в себе команду для установки тестовой конфигурации 1с с ключами, используется в 
***srvr1c_test_service_name***  
Переменная объявлена в default/main.yml, содержит в себе краткое название сервиса 1с тестового, используется в 
***srvr1c_test_full_service_name***  
Переменная объявлена в default/main.yml, содержит в себе полное название сервиса 1с тестового, используется в 
***srvr1c_test_serice_port***  
Переменная объявлена в default/main.yml, содержит в себе адрес порта который будет слушать тестовый 1с, используется в 
***srvr1c_test_database_name***  
Переменная объявлена в default/main.yml, содержит в себе название базы данных которая будет создана для тествой конфигурации 1с, используется в 
***srvr1c_test_service_user***  
Переменная объявлена в default/main.yml, содержит в себе название юзера который будет управлять тестовым 1с, используется в 
***srvr1c_test_templates_service***  
Переменная объявлена в default/main.yml, содержит в себе директории с конфигурационными файлами для сервиса 1с тестовой конфигурации, используется в 
***srvr1c_test_shell_check_service_status***  
Переменная объявлена в default/main.yml, содержит в себе команду для проверку статуса сервиса 1с, используется в 
############# TEST #############

***srvr1c_debug_status***  
Переменная объявлена в default/main.yml, содержит в себе значение которое отвечает за дебаг результатов на определённых этапах, используется в 

***srv1c_hosts***  
Переменная объявлена в default/main.yml, содержит в себе значение группы машин на которых раскатывается роль, используется в 

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

# Установка роли

Для раскатки роли необходимо перенести архив с сервисными пакетами:

- sentinel/Sentinel_LDK_Linux_Run-time_Installer_script.tar.gz
- server64_8_3_23_2236.tar.gz
- setup-training-8.3.25.1257-x86_64.run
- training_8_3_25_1257_LinuxRun.tar.gz

Эти сервисные пакеты позволят прокинуть необходимые зависимости, а также содержат необходимые сервисы для отработки роли.

## Настройки роли

Для того чтобы роль раскаталась с Вашими сервисными настройками, необходимо поменять значения данных переменных:

| Наименование переменной                          | Значение по умолчанию                  | Предназначение                                               |
|------------------------------------------------|---------------------------------------|------------------------------------------------------------|
| {{ srvr1c_artifactory_directory }}           | 1c_install_2v                      | Папка с архивами и пакетами в tmp/1c_install_2v         |
| {{ srvr1c_rac_port }}                        | 1545                                | Порт сервиса RAC                                           |
| {{ srvr1c_cluster_admin_login }}             | admin                               | Логин админа RAC                                          |
| {{ srvr1c_cluster_admin_pass }}              | admin                               | Пароль админа RAC                                         |
| {{ srvr1c_pgadmin_email }}                   | test@gmail.com                     | Адрес для аутентификации в pgAdmin4                       |
| {{ srvr1c_pgadmin_pass }}                    | TestAdmin1234                      | Пароль для аутентификации в pgAdmin4                      |
| {{ srvr1c_postgresql_db_descr }}             | Decription_BP_db                   | Описание БД                                               |
| {{ srvr1c_postgresql_db_name }}              | my_db                              | Название БД                                               |
| {{ srvr1c_postgresql_user }}                 | postgres                            | Наименование юзера БД                                     |
| {{ srvr1c_postgresql_group }}                | postgres                            | Наименование группы БД                                    |
| {{ srvr1c_postgresql_psql_pass }}            | postgresql                          | Пароль для оболочки psql                                   |
| {{ srvr1c_postgresql_addr }}                 | {{ ansible_default_ipv4.address }} | Адрес, на котором опубликована БД                          |
| {{ srvr1c_postgresql_port }}                 | 5432                                | Порт, на котором опубликована БД                           |
| {{ srvr1c_postgresql_addr_subnet }}          | 192.168.80.0/24                     | Маска подсети с адресом для доступа к БД                  |
| {{ srvr1c_apache_webservice_addr }}          | {{ ansible_default_ipv4.address }} | Адрес всех сервисов Apache, на которых разворачиваются сервисы |

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

***Start role***  
**Раскатка prod контура**  

    - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml  

**Раскатка test контура**  

    - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml --extra-vars "srvr1c_traning_use=true"  

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
