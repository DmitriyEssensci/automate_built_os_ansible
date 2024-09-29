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
  Переменная объявлена в default/main.yml, содержит
- grafana_download_pgp    
  Переменная объявлена в default/main.yml, содержит
- grafana_repo    
  Переменная объявлена в default/main.yml, содержит

- grafana_dest_gpg    
  Переменная объявлена в default/main.yml, содержит
- grafana_convert_gpg   
  Переменная объявлена в default/main.yml, содержит

- grafana_check_version   
  Переменная объявлена в default/main.yml, содержит
- grafana_service_status    
  Переменная объявлена в default/main.yml, содержит

- grafana_config_file   
  Переменная объявлена в default/main.yml, содержит

- grafana_dashboard_path    
  Переменная объявлена в default/main.yml, содержит
- grafana_dashboard_main_dashboard_name   
  Переменная объявлена в default/main.yml, содержит
- grafana_dashboard_main_dashboard_dir    
  Переменная объявлена в default/main.yml, содержит

- grafana_host_address    
  Переменная объявлена в default/main.yml, содержит

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