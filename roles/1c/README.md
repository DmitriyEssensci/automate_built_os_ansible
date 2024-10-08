# Роль 1с
------------

Данная роль позволяет установить 1С со всеми зависимыми сервисами. Настраиваются тонкий, толстый и веб-клиенты, устанавливается PostgreSQL, Apache2, HASP, а также создаётся "тестовый" контур, который устанавливает тестовую конфигурацию 1С.

## Требования
------------

### Установка роли

Для раскатки роли необходимо перенести архив с сервисными пакетами:

- sentinel/Sentinel_LDK_Linux_Run-time_Installer_script.tar.gz
- server64_8_3_23_2236.tar.gz
- training_8_3_25_1257_LinuxRun.tar.gz

Эти сервисные пакеты позволят прокинуть необходимые зависимости, а также содержат необходимые сервисы для отработки роли.

### Настройки роли

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

## Команды RAC
--------------

- Вывод пользователей кластера:
	rac profile list --cluster=96f390a2-63f7-11ef-5794-000c296fd51b 
	rac profile list --cluster=36e16260-4e52-43c7-8644-3ef4c2b92888
	
- Вывод всех информационных баз:
	rac infobase summary list  --cluster=96f390a2-63f7-11ef-5794-000c296fd51b --cluster-user=admin --cluster-pwd=admin
	rac infobase summary list  --cluster=36e16260-4e52-43c7-8644-3ef4c2b92888 --cluster-user=admin --cluster-pwd=admin
	
- Создание информационной базы:
	rac infobase create \
	  --cluster=96f390a2-63f7-11ef-5794-000c296fd51b \
	  --cluster-user=admin \
	  --cluster-pwd=admin \
	  --create-database \
	  --name=my_db \
	  --descr=test_descr \
	  --dbms=PostgreSQL \
	  --db-server=192.168.80.129 \
	  --db-name=my_db \
	  --locale=ru \
	  --db-user=postgres \
	  --db-pwd=postgresql \
	  --license-distribution=allow \
	  --scheduled-jobs-deny=on
	rac infobase create \
	  --cluster=36e16260-4e52-43c7-8644-3ef4c2b92888 \
	  --cluster-user=admin \
	  --cluster-pwd=admin \
	  --create-database \
	  --name=my_db \
	  --descr=test_descr \
	  --dbms=PostgreSQL \
	  --db-server=192.168.80.136 \
	  --db-name=my_db \
	  --locale=ru \
	  --db-user=postgres \
	  --db-pwd=postgresql \
	  --license-distribution=allow \
	  --scheduled-jobs-deny=on
	  
- Удаление бд:
	rac infobase drop --cluster=96f390a2-63f7-11ef-5794-000c296fd51b --infobase=c649c154-3557-4103-8364-f84fe9fe6bca --infobase-user=postgres --infobase-pwd=postgresql  --cluster-user=admin --cluster-pwd=admin --drop-database
	rac infobase drop --cluster=36e16260-4e52-43c7-8644-3ef4c2b92888 --infobase=1d30885c-73b0-4c6d-82e4-a8b54f9a41eb --infobase-user=postgres --infobase-pwd=postgresql  --cluster-user=admin --cluster-pwd=admin --drop-database
	
- Вывод информации об админах:
	rac cluster admin list --cluster=96f390a2-63f7-11ef-5794-000c296fd51b --cluster-user=admin --cluster-pwd=admin
	rac cluster admin list --cluster=36e16260-4e52-43c7-8644-3ef4c2b92888 --cluster-user=admin --cluster-pwd=admin
	
- Регистрация админа:
	rac cluster admin --cluster=96f390a2-63f7-11ef-5794-000c296fd51b register --name=admin --pwd=admin --descr=my-admin  --auth=pwd
	rac cluster admin --cluster=36e16260-4e52-43c7-8644-3ef4c2b92888 register --name=admin --pwd=admin --descr=my-admin  --auth=pwd
	
- Удаление админа:
	rac cluster admin remove --cluster=96f390a2-63f7-11ef-5794-000c296fd51b --name=admin  --cluster-user=admin --cluster-pwd=admin
	rac cluster admin remove --cluster=36e16260-4e52-43c7-8644-3ef4c2b92888 --name=admin  --cluster-user=admin --cluster-pwd=admin

## Переменные Роли
--------------

Описание настраиваемых переменных для этой роли должно находиться здесь, включая любые переменные, которые находятся в defaults/main.yml, vars/main.yml, и любые переменные, которые могут/должны быть установлены через параметры роли. Любые переменные, которые читаются из других ролей и/или глобальной области (например, hostvars, group vars и т.д.) также следует упомянуть здесь.

- srvr1c_traning_use  
  Переменная объявлена в defaults/main.yml, содержит пустое значение для запуска плейбука с экстра параметром true/false, используется в.

- srvr1c_service_name  
  Переменная объявлена в defaults/main.yml, содержит краткое название сервиса 1С, используется в.

- srvr1c_full_service_name  
  Переменная объявлена в defaults/main.yml, содержит полное название сервиса 1С, используется в.

- srvr1c_ras_service_name  
  Переменная объявлена в defaults/main.yml, содержит краткое название сервиса RAS, используется в.

- srvr1c_full_ras_service_name  
  Переменная объявлена в defaults/main.yml, содержит полное название сервиса RAS, используется в.

- srvr1c_version  
  Переменная объявлена в defaults/main.yml, содержит версию пакета 1С для установки, используется в.

- srvr1c_destination  
  Переменная объявлена в defaults/main.yml, содержит директорию, куда будет устанавливаться 1С на сервере, используется в.

- srvr1c_services_destination  
  Переменная объявлена в defaults/main.yml, содержит директорию, куда будут устанавливаться сервисы 1С на сервере, используется в.

- srvr1c_artifactory_directory  
  Переменная объявлена в defaults/main.yml, содержит название папки-хранилища, в которой лежат все пакеты для установки, используется в.

- srvr1c_run_files  
  Переменная объявлена в defaults/main.yml, содержит название архива, где лежит .run файл пакета 1С, используется в.

- srvr1c_setup_run_file  
  Переменная объявлена в defaults/main.yml, содержит название установочного пакета 1С, используется в.

- srvr1c_rac_sys_dir  
  Переменная объявлена в defaults/main.yml, содержит системную директорию для сервиса RAS, используется в.

- srvr1c_rac_user  
  Переменная объявлена в defaults/main.yml, содержит название пользователя для RAS, используется в.

- srvr1c_rac_group  
  Переменная объявлена в defaults/main.yml, содержит название группы для RAS, используется в.

- srvr1c_rac_port  
  Переменная объявлена в defaults/main.yml, содержит номер порта для сервиса RAS, используется в.

- srvr1c_sentinel_fullnes_archive_file_name  
  Переменная объявлена в defaults/main.yml, содержит название архива, где лежат пакеты для установки сервисов HASP и AKSUSBD, используется в.

- srvr1c_sentinel_pkg_archive_file_name  
  Переменная объявлена в defaults/main.yml, содержит название директории, где лежат установочные пакеты для AKSUSBD, используется в.

- srvr1c_sentinel_tmp_dir  
  Переменная объявлена в defaults/main.yml, содержит название директории с пакетами Sentinel, используется в.

- srvr1c_sentinel_fullnes_archive_dir  
  Переменная объявлена в defaults/main.yml, содержит название директории, куда перемещаются разархированные пакеты Sentinel, используется в.

- srvr1c_sentinel_pkg_archive_dir  
  Переменная объявлена в defaults/main.yml, содержит название директории, куда перемещаются разархированные пакеты Sentinel для сервиса AKSUSBD, используется в.

- srvr1c_aksusbd_service  
  Переменная объявлена в defaults/main.yml, содержит полное название сервиса AKSUSBD, используется в.

- srvr1c_hasp_service  
  Переменная объявлена в defaults/main.yml, содержит полное название сервиса HASPLMD, используется в.

- srvr1c_default_locale  
  Переменная объявлена в defaults/main.yml, содержит название локалей, которые будут устанавливаться по умолчанию, используется в.

- srvr1c_locales_files  
  Переменная объявлена в defaults/main.yml, содержит переменные для работы с локалями, используется в.

  - locale_gen  
    Переменная объявлена в defaults/main.yml, содержит название директории до генерационного файла локалей, используется в.

  - locale_conf  
    Переменная объявлена в defaults/main.yml, содержит название директории до конфигурационного файла локалей, используется в.

- srvr1c_locales  
  Переменная объявлена в defaults/main.yml, содержит название локалей, которые будут выставлены, используется в.

- srvr1c_locale_path  
  Переменная объявлена в defaults/main.yml, содержит путь к исполняемому сервису, отвечающему за локали, используется в.

- srvr1c_shell_check_rac_service_status  
  Переменная объявлена в defaults/main.yml, содержит команду, которая проверяет статус RAS сервиса, используется в.

- srvr1c_shell_rac_add_admin  
  Переменная объявлена в defaults/main.yml, содержит команду, которая устанавливает админа по умолчанию с его учётными данными в RAS сервер, используется в.

- srvr1c_shell_rac_get_admin_info  
  Переменная объявлена в defaults/main.yml, содержит команду, которая выводит всю информацию об админах в RAS, используется в.

- srvr1c_shell_rac_get_infobase  
  Переменная объявлена в defaults/main.yml, содержит команду, которая выводит всю информацию о БД, которые установлены в RAS, используется в.

- srvr1c_shell_rac_drop_db  
  Переменная объявлена в defaults/main.yml, содержит команду, которая удаляет БД, используется в.

- srvr1c_shell_rac_create_db  
  Переменная объявлена в defaults/main.yml, содержит команду, которая создаёт БД, используется в.

- srvr1c_shell_rac_check_db_list  
  Переменная объявлена в defaults/main.yml, содержит команду, которая выводит всю информацию о базах данных в списке, используется в.

- srvr1c_shell_rac_get_general_cluster_info  
  Переменная объявлена в defaults/main.yml, содержит команду, которая выводит всю информацию по кластеру, используется в.

- srvr1c_shell_rac_start_cluster  
  Переменная объявлена в defaults/main.yml, содержит команду, которая запускает демон кластера, используется в.

- srvr1c_shell_check_timezone  
  Переменная объявлена в defaults/main.yml, содержит команду, которая проверяет правильную таймзону, используется в.

- srvr1c_shell_check_service_status  
  Переменная объявлена в defaults/main.yml, содержит команду, которая проверяет статус сервиса 1С, используется в.

- srvr1c_shell_install_1c  
  Переменная объявлена в defaults/main.yml, содержит команду, которая устанавливает 1С с ключами, используется в.

- srvr1c_shell_fix_broken_package  
  Переменная объявлена в defaults/main.yml, содержит команду, которая устраняет неисправности в связях после/перед установкой пакетов, используется в.

- srvr1c_shell_set_timezone  
  Переменная объявлена в defaults/main.yml, содержит команду, которая устанавливает правильные таймзоны, используется в.

- srvr1c_shell_create_server_simlink  
  Переменная объявлена в defaults/main.yml, содержит команду, которая проводит симлинки с сервисом 1С, используется в.

- srvr1c_shell_create_ras_simlink  
  Переменная объявлена в defaults/main.yml, содержит команду, которая проводит симлинки с сервисом RAS, используется в.

- srvr1c_shell_service_check  
  Переменная объявлена в defaults/main.yml, содержит команду, которая проверяет статус всех установленных сервисов 1С, используется в.

- srvr1c_shell_postgresql_conf_postgresql_path  
  Переменная объявлена в default/main.yml, содержит команду, которая запускается в оболочке psql и выполняет запрос на вывод конфигурационного файла - postgresql. Используется в ...

- srvr1c_shell_postgresql_conf_pg_hba_path  
  Переменная объявлена в default/main.yml, содержит команду, которая запускается в оболочке psql и выполняет запрос на вывод конфигурационного файла - pg_hba. Используется в ...

- srvr1c_shell_check_postgresql_status  
  Переменная объявлена в default/main.yml, содержит команду, которая проверяет статус сервиса postgrespro-1c-14. Используется в ...

- srvr1c_shell_install_sentinel 
  Переменная объявлена в default/main.yml, содержит команду, которая устанавливает сервисы hasp методами dpkg. Используется в ...

- srvr1c_shell_check_aksusbd_status   
  Переменная объявлена в default/main.yml, содержит команду, которая проверяет статус сервиса aksusbd. Используется в ...

- srvr1c_shell_check_hasplmd_status   
  Переменная объявлена в default/main.yml, содержит команду, которая проверяет статус сервиса hasplmd. Используется в ...

- srvr1c_shell_check_apache2_status   
  Переменная объявлена в default/main.yml, содержит команду, которая проверяет статус сервиса apache2. Используется в ...

- srvr1c_templates_service    
  Переменная объявлена в default/main.yml, содержит директории для перемещения сервисных файлов, связанных с сервисом 1С. Используется в ...

- srvr1c_templates_ras_service    
  Переменная объявлена в default/main.yml, содержит директории для перемещения сервисных файлов, связанных с сервисом RAC. Используется в ...

- srvr1c_cluster_admin_login    
  Переменная объявлена в default/main.yml, содержит учётные данные в виде логина для администратора кластера RAC. Используется в ...

- srvr1c_cluster_admin_pass   
  Переменная объявлена в default/main.yml, содержит учётные данные в виде пароля для администратора кластера RAC. Используется в ...

- srvr1c_cluster_database_type    
  Переменная объявлена в default/main.yml, содержит тип базы данных для кластера RAC. Используется в ...

- srvr1c_pgadmin_email    
  Переменная объявлена в default/main.yml, содержит email для доступа к интерфейсу сервиса pgadmin4. Используется в ...

- srvr1c_pgadmin_pass   
  Переменная объявлена в default/main.yml, содержит пароль для доступа к интерфейсу сервиса pgadmin4. Используется в ...

- srvr1c_postgresql_locale    
  Переменная объявлена в default/main.yml, содержит локаль postgresql для установки в базу данных. Используется в ...

- srvr1c_postgresql_license_distribution    
  Переменная объявлена в default/main.yml, содержит значение включения лицензионного соглашения. Используется в ...

- srvr1c_postgresql_scheduled_jobs    
  Переменная объявлена в default/main.yml, содержит значение включения шедулера на джобу. Используется в ...

- srvr1c_postgresql_db_descr    
  Переменная объявлена в default/main.yml, содержит краткое описание для базы данных. Используется в ...

- srvr1c_postgresql_db_name   
  Переменная объявлена в default/main.yml, содержит наименование базы данных. Используется в ...

- srvr1c_postgresql_user    
  Переменная объявлена в default/main.yml, содержит логин пользователя Postgresql. Используется в ...

- srvr1c_postgresql_group   
  Переменная объявлена в default/main.yml, содержит группу пользователя Postgresql. Используется в ...

- srvr1c_postgresql_psql_pass   
  Переменная объявлена в default/main.yml, содержит пароль пользователя Postgresql. Используется в ...

- srvr1c_postgresql_package_name    
  Переменная объявлена в default/main.yml, содержит название пакета postgresql, который устанавливается. Используется в ...

- srvr1c_postgresql_addr    
  Переменная объявлена в default/main.yml, содержит адрес postgresql, на котором будут хоститься базы данных. Используется в ...

- srvr1c_postgresql_port    
  Переменная объявлена в default/main.yml, содержит порт postgresql, на котором будут хоститься базы данных. Используется в ...

- srvr1c_postgresql_service   
  Переменная объявлена в default/main.yml, содержит название сервиса postgresql. Используется в ...

- srvr1c_postgresql_conf_dir    
  Переменная объявлена в default/main.yml, содержит путь к директории с конфигурационными файлами для postgresql. Используется в ...

- srvr1c_postgresql_conf_file   
  Переменная объявлена в default/main.yml, содержит конфигурационный файл для postgresql. Используется в ...

- srvr1c_postgresql_repo_url    
  Переменная объявлена в default/main.yml, содержит репозиторий, откуда скачиваются метаданные для установки в систему. Используется в ...

- srvr1c_postgresql_repo_dest   
  Переменная объявлена в default/main.yml, содержит директорию, куда будет прописываться репозиторий. Используется в ...

- srvr1c_templates_postgresql_conf_file   
  Переменная объявлена в default/main.yml, содержит директории для перемещения конфигурационных файлов для сервиса postgresql. Используется в ...

- srvr1c_postgresql_addr_subnet   
  Переменная объявлена в default/main.yml, содержит только маску подсети для настройки сервиса postgresql. Используется в ...

- srvr1c_postgresql_subnet    
  Переменная объявлена в default/main.yml, содержит сетевую настройку маски подсети для конфигурационного файла postgresql. Используется в ...

- srvr1c_apache_service   
  Переменная объявлена в default/main.yml, содержит название сервиса apache2. Используется в ...

- srvr1c_apache_webservice_name   
  Переменная объявлена в default/main.yml, содержит название веб-сервиса 1С, который будет доступен под данным именем. Используется в ...

- srvr1c_apache_webservice_addr   
  Переменная объявлена в default/main.yml, содержит адрес веб-сервиса 1С и всех сервисов, на котором apache2 будет поднимать сервисы. Используется в ...

- srvr1c_apache_vrd_dir   
  Переменная объявлена в default/main.yml, содержит директорию с веб-сервисом 1С. Используется в ...

- srvr1c_apache_conf_file   
  Переменная объявлена в default/main.yml, содержит конфигурационный файл apache2. Используется в ...

- srvr1c_apache_publish_webinst   
  Переменная объявлена в default/main.yml, содержит команду для запуска веб-сервиса 1С на apache2 через веб-клиент 1С. Используется в ...

---

### ############# TEST #############

- srvr1c_test_version   
  Переменная объявлена в default/main.yml, содержит версию 1С для тестовой конфигурации. Используется в ...

- srvr1c_test_destination   
  Переменная объявлена в default/main.yml, содержит путь, куда будет установлена тестовая конфигурация 1С. Используется в ...

- srvr1c_test_run_files   
  Переменная объявлена в default/main.yml, содержит название архива для установки тестовой конфигурации 1С. Используется в ...

- srvr1c_test_setup_run_file    
  Переменная объявлена в default/main.yml, содержит название .run файла для установки тестовой конфигурации 1С. Используется в ...

- srvr1c_test_shell_install_1c    
  Переменная объявлена в default/main.yml, содержит команду для установки тестовой конфигурации 1С с ключами. Используется в ...

- srvr1c_test_service_name    
  Переменная объявлена в default/main.yml, содержит краткое название тестового сервиса 1С. Используется в ...

- srvr1c_test_full_service_name   
  Переменная объявлена в default/main.yml, содержит полное название тестового сервиса 1С. Используется в ...

- srvr1c_test_service_port    
  Переменная объявлена в default/main.yml, содержит адрес порта, который будет слушать тестовый 1С. Используется в ...

- srvr1c_test_database_name   
  Переменная объявлена в default/main.yml, содержит название базы данных, которая будет создана для тестовой конфигурации 1С. Используется в ...

- srvr1c_test_service_user    
  Переменная объявлена в default/main.yml, содержит название пользователя, который будет управлять тестовым 1С. Используется в ...

- srvr1c_test_templates_service   
  Переменная объявлена в default/main.yml, содержит директории с конфигурационными файлами для сервиса 1С тестовой конфигурации. Используется в ...

- srvr1c_test_shell_check_service_status    
  Переменная объявлена в default/main.yml, содержит команду для проверки статуса сервиса 1С. Используется в ...

### ############# TEST #############

- srvr1c_debug_status   
  Переменная объявлена в default/main.yml, содержит значение, которое отвечает за дебаг результатов на определённых этапах. Используется в ...

- srv1c_hosts   
  Переменная объявлена в default/main.yml, содержит значение группы машин, на которых раскатывается роль. Используется в ...

Зависимости
-----------

Здесь должен быть указан список других ролей, размещённых на Galaxy, а также любые детали, касающиеся параметров, которые могут быть установлены для других ролей, или переменные, используемые из других ролей.

Пример Playbook
---------------

Пример использования роли (например, с переменными, передаваемыми в качестве параметров):

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

## Запуск роли
### Разворачивание prod окружения

    - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml  

### Разворачивание test окружения

    - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml --extra-vars "srvr1c_traning_use=true"  

Лицензия
--------

BSD

Информация об авторе
--------------------

Опциональный раздел для указания контактной информации автора роли или сайта (HTML не допускается).