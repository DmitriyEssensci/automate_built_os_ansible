# Роль grafana
------------

Данная роль позволяет установить сервис grafana, а так же настроить его.

Краткое описание роли здесь.

## Требования
------------

## Переменные Роли
--------------

Описание настраиваемых переменных для этой роли должно находиться здесь, включая любые переменные, которые находятся в defaults/main.yml, vars/main.yml, и любые переменные, которые могут/должны быть установлены через параметры роли. Любые переменные, которые читаются из других ролей и/или глобальной области (например, hostvars, group vars и т.д.) также следует упомянуть здесь.

- grafana_ensure_keyrings   
  Переменная объявлена в default/main.yml, содержит в себе директорию для pgp ключей, используется в tasks/main.yml
- grafana_download_pgp    
  Переменная объявлена в default/main.yml, содержит в себе ссылку на pgp ключ сервиса, используется в tasks/main.yml
- grafana_repo    
  Переменная объявлена в default/main.yml, содержит в себе данные о репозитории, используется в tasks/main.yml
- grafana_dest_gpg    
  Переменная объявлена в default/main.yml, содержит название файла с pgp ключом, используется в tasks/main.yml
- grafana_convert_gpg   
  Переменная объявлена в default/main.yml, содержит команду для конвертации pgp ключа, используется в tasks/main.yml
- grafana_service_name    
  Переменная объявлена в default/main.yml, содержит краткое название сервиса, используется в tasks/main.yml

- grafana_check_version   
  Переменная объявлена в default/main.yml, содержит команду, которая проверяет версию grafana, используется в tasks/main.yml
- grafana_check_service_status    
  Переменная объявлена в default/main.yml, содержит команду, которая проверяет статус службы grafana, используется в tasks/main.yml

- grafana_user    
  Переменная объявлена в default/main.yml, содержит наименование юзера grafana, используется в tasks/main.yml
- grafana_group   
  Переменная объявлена в default/main.yml, содержит наименование группы grafana, используется в tasks/main.yml

- grafana_name    
  Переменная объявлена в default/main.yml, содержит наименование пакета, используется в tasks/main.yml
- grafana_ssl_crt   
  Переменная объявлена в default/main.yml, содержит наименование файла сертификата, используется в tasks/main.yml
- grafana_ssl_key   
  Переменная объявлена в default/main.yml, содержит наименование файла ключа для сертификата, используется в tasks/main.yml
- grafana_ssl_dir   
  Переменная объявлена в default/main.yml, содержит директорию отведённую для ssl сертификатов, используется в tasks/main.yml

- grafana_config_host_address   
  Переменная объявлена в default/main.yml, содержит адрес сервиса, используется в templates/etc/grafana/grafana.ini.j2, tasks/main.yml
- grafana_config_file   
  Переменная объявлена в default/main.yml, содержит директорию и файл сервиса grafana, используется в templates/etc/grafana/grafana.ini.j2, tasks/main.yml
- grafana_config_protocol   
  Переменная объявлена в default/main.yml, содержит наименование протокола на котором разворачивается сервис, используется в templates/etc/grafana/grafana.ini.j2, tasks/main.yml
- grafana_config_port   
  Переменная объявлена в default/main.yml, содержит номер порта на котором разворачивается сервис, используется в templates/etc/grafana/grafana.ini.j2, tasks/main.yml

- grafana_dashboard_path    
  Переменная объявлена в default/main.yml, содержит директорий с дашбордом, используется в tasks/main.yml
- grafana_dashboard_main_dashboard_name   
  Переменная объявлена в default/main.yml, содержит файл дашборда, используется в tasks/main.yml
- grafana_dashboard_main_dashboard_dir    
  Переменная объявлена в default/main.yml, содержит директорию с файлом дашборда, используется в templates/etc/grafana/grafana.ini.j2, tasks/main.yml

- grafana_host_address    
  Переменная объявлена в playbooks/grafana.yml, содержит название хост группы.

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

    - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/install_apps.yml

Лицензия
--------

BSD

Информация об авторе
--------------------

Опциональный раздел для указания контактной информации автора роли или сайта (HTML не допускается).