# Роль 1с
------------

Данная роль позволяет установить мониториг prometheus, node_exporter.

## Требования
------------

## Переменные Роли
--------------

Описание настраиваемых переменных для этой роли должно находиться здесь, включая любые переменные, которые находятся в defaults/main.yml, vars/main.yml, и любые переменные, которые могут/должны быть установлены через параметры роли. Любые переменные, которые читаются из других ролей и/или глобальной области (например, hostvars, group vars и т.д.) также следует упомянуть здесь.

### prometheus
- prometheus_version  
  Переменная объявлена в defaults/main.yml, содержит  
- prometheus_download_url  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_archive  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_system_dir  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_conf_dir  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_service_bin_dir  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_bin_dir  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_lib_dir  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_bin_file  
  Переменная объявлена в defaults/main.yml, содержит
    - prometheus  
      Переменная объявлена в defaults/main.yml, содержит
    - promtool  
      Переменная объявлена в defaults/main.yml, содержит
- prometheus_conf_file  
  Переменная объявлена в defaults/main.yml, содержит
    - consoles   
      Переменная объявлена в defaults/main.yml, содержит
    - console_libraries   
      Переменная объявлена в defaults/main.yml, содержит
- prometheus_service_conf_file  
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_service_name   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_template_service_systemd   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_template_prometheus_yml    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_check_service_status   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_port   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_user   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_group    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_python_interpreter   
  Переменная объявлена в defaults/main.yml, содержит

- prometheus_host_machine   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_grafana_host_address   
  Переменная объявлена в defaults/main.yml, содержит

- prometheus_prometheusconf   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_scinterval   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_scrape_interval    
  Переменная объявлена в defaults/main.yml, содержит

- prometheus_name   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_ssl_crt    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_ssl_key    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_ssl_dir    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_ssl_network_conf   
  Переменная объявлена в defaults/main.yml, содержит

### node_exporter
- prometheus_node_exporter_name   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_ssl_crt    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_ssl_key    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_ssl_dir    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_ssl_network_conf   
  Переменная объявлена в defaults/main.yml, содержит

- prometheus_node_exporter_port   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_version    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_download_url   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_archive    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_system_dir   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_service_name   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_node_exporter_check_service_status   
  Переменная объявлена в defaults/main.yml, содержит

- prometheus_template_service_systemd_node    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_template_default_options_node    
  Переменная объявлена в defaults/main.yml, содержит

### victoriametrics
- prometheus_victoriametrics_user   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_victoriametrics_group    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_victoriametrics_var_dir    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_victoriametrics_run_dir    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_victoriametrics_bin_dir    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_victoriametrics_status   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_victoriametrics_service_name   
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_template_victoriametrics_service_systemd_node    
  Переменная объявлена в defaults/main.yml, содержит
- prometheus_vm_remote_write  
  Переменная объявлена в defaults/main.yml, содержит
    - url   
      Переменная объявлена в defaults/main.yml, содержит
    - username    
      Переменная объявлена в defaults/main.yml, содержит
    - password    
      Переменная объявлена в defaults/main.yml, содержит

- prometheus_hosts    
  Переменная объявлена в defaults/main.yml, содержит

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

    ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/prometheus.yml

Лицензия
--------

BSD

Информация об авторе
--------------------

Опциональный раздел для указания контактной информации автора роли или сайта (HTML не допускается).
