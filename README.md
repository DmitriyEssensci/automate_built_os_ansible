# Репозиторий automate_built_os_ansible

Репозиторий с IaC решением по установке сервисов, программного обеспечения и пакетов, а также настройке конфигураций системы.

## Создание роли

Пример команды для создания новой роли с заданной структурой, которая является стандартом написания роли:

- ansible-galaxy init role_name

## Роли

В данном репозитории предоставлены следующие роли, которые доступны для раскатки. Каждая роль и плейбук соответствует сервису по названию.

| Плейбук                     | Название роли      | Название сервиса/пакета                            | Тип системы для установки |
|-----------------------------|-------------------|---------------------------------------------------|---------------------------|
| playbooks/1c.yml             | 1c                | 1С, PostgreSQL, HASP, Apache, RAC                  | bare-metal                 |
| playbooks/adduser.yml        | adduser           | -                                                 | bare-metal                 |
| playbooks/check_system.yml   | check_system      | -                                                 | bare-metal                 |
| playbooks/grafana.yml        | grafana           | Grafana                                           | bare-metal                 |
| playbooks/install_apps.yml   | install_apps      | {{ installapps_apps_list }}                       | bare-metal                 |
| playbooks/jenkins.yml        | jenkins           | Jenkins                                           | bare-metal                 |
| playbooks/prometheus.yml     | prometheus        | Prometheus, node_exporter                         | bare-metal                 |

## Контуры

В данном репозитории предоставлены следующие контуры для раскатки хостов:

- integration
- production

## Группы хостов

Группы хостов разделены по контурам:

### Контур integration:
- all
- newmachines -> new_machines:children

### Контур production:
- all
- mainserver -> main_server:children

## Последовательность запуска ролей

Рекомендованный список запуска ролей для проверки системы, установки ПО и сервисов для конфигурирования полного комплекса пакетов для 1С сервера:

| Название роли   | Команда для запуска (bash)                                                                 |
|-----------------|---------------------------------------------------------------------------------------------|
| check_system    | ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/check_system.yml |
| install_apps    | ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/install_apps.yml |
| jenkins         | ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/jenkins.yml |
| prometheus      | ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/prometheus.yml |
| grafana         | ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/grafana.yml |
| 1c              | ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/1c.yml |

### Примечание 1: Для установки Grafana требуется VPN-подключение, либо .deb пакет Grafana, который должен находиться по пути /tmp/grafana-enterprise_11.2.0_amd64.deb.

### Примечание 2: При установке сервисов мониторинга на клиентские виртуальные или bare-metal машины необходимо установить переменные {{ prometheus_host_machine }} и {{ prometheus_grafana_host_address }} на hostname хоста для Prometheus и его IPv4 адрес.

## Список сервисов, развёрнутых по адресу/доменному имени и порту

| Название сервиса/подсервиса     | Полный адрес сервера с портом                    | Учётные данные                          |
|---------------------------------|--------------------------------------------------|------------------------------------------|
| Prometheus                      | http://hostname_ip:9090                          | -                                        |
| node_exporter                   | http://hostname_ip:9100/metrics                  | -                                        |
| Grafana                         | http://hostname_ip:3000                          | login/pass: admin/admin                  |
| Grafana API                     | http://{{ prometheus_grafana_host_address }}:3000/api/prom/push | -                                        |
| Jenkins                         | http://hostname_ip:8080                          | login/pass: admin/admin                  |
| Apache-Web (1С)                 | http://hostname_ip/{{ srvr1c_postgresql_db_name }}/ru_RU/ | УЗ пользователя БД                      |
| ragent                          | 1540                                             | -                                        |
| RAC                             | 1545                                             | -                                        |
| RAC Cluster                     | 1541                                             | -                                        |
| Apache2                         | 80                                               | -                                        |
| PostgreSQL                      | http://hostname_ip:5432/                         | login/pass: postgres/postgresql          |