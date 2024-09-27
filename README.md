# Репозиторий automate_built_os_ansible

Репозиторий с IaC решением по установке сервисов, программного обеспечения и пакетов, а также настройке конфигураций системы.

## Требования

- Ansible версии 2.9 и выше
- Python 3.x
- Доступ по SSH к управляемым хостам

## Предварительная подготовка

1. Настройте файл inventory с данными о хостах.
2. Обновите значения переменных в плейбуках согласно вашему окружению.
3. Убедитесь, что у вас есть доступ к VPN (если требуется для установки Grafana).
4. Если используется Ansible Vault, создайте или получите необходимые файлы с зашифрованными переменными.

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

- Примечание 1: Для установки Grafana требуется VPN-подключение, либо .deb пакет Grafana, который должен находиться по пути /tmp/grafana-enterprise_11.2.0_amd64.deb.
- Примечание 2: При установке сервисов мониторинга на клиентские виртуальные или bare-metal машины необходимо установить значение переменных с {{ prometheus_host_machine }} и {{ prometheus_grafana_host_address }} на {{ hostname хоста для Prometheus }} и {{ его IPv4 адрес }}.

## Список сервисов, развёрнутых по адресу/доменному имени и порту

| Название сервиса/подсервиса     | Полный адрес сервера с портом                    | Учётные данные                          |
|---------------------------------|--------------------------------------------------|------------------------------------------|
| Prometheus                      | http://hostname_ip:9090                          | -                                        |
| node_exporter                   | http://hostname_ip:9100/metrics                  | -                                        |
| Grafana                         | http://{{ prometheus_grafana_host_address }}:3000                          | login/pass: admin/admin                  |
| Grafana API                     | http://{{ prometheus_grafana_host_address }}:3000/api/prom/push | -                                        |
| Jenkins                         | http://hostname_ip:8080                          | login/pass: admin/admin                  |
| Apache-Web (1С)                 | http://hostname_ip/{{ srvr1c_postgresql_db_name }}/ru_RU/ | УЗ пользователя БД                      |
| ragent                          | 1540                                             | -                                        |
| RAC                             | 1545                                             | -                                        |
| RAC Cluster                     | 1541                                             | -                                        |
| Apache2                         | 80                                               | -                                        |
| PostgreSQL                      | http://hostname_ip:5432/                         | login/pass: postgres/postgresql          |

## Что следует добавить?

1. Чистый код: Для более читабельного и поддерживаемого кода рекомендуется придерживаться лучших практик написания Ansible плейбуков:
   - Используйте осмысленные названия для ролей и переменных.
   - Следите за тем, чтобы каждый плейбук был независимым и легко поддерживался.
   - Проверяйте синтаксис команд перед коммитами с помощью ansible-lint и yamllint.

2. Документирование изменений: При каждом изменении ролей или плейбуков будет полезно добавлять комментарии и обновлять документацию, чтобы вся команда могла легко отслеживать изменения.

3. Практики работы с Git:
   - Рассмотрите использование семантических сообщений коммитов, чтобы история изменений была понятной.
   - Применяйте feature-ветки для разработки новых ролей или изменений.
   - Регулярное тестирование плейбуков перед слиянием в основную ветку (например, с помощью CI/CD) станет хорошей практикой.

4. Оптимизация и безопасность: Использование Ansible Vault для шифрования чувствительных данных и минимизация использования общих или небезопасных переменных помогут улучшить безопасность проекта. Разделение настроек по окружениям также будет полезным для предотвращения случайного запуска на продакшене.

5. Требования: Будет полезно создать раздел с минимальными версиями Ansible, Python и других зависимостей, чтобы упростить настройку окружения для новых участников проекта.

6. Предварительная подготовка: Упомяните важные действия, которые необходимо выполнить до запуска плейбуков, такие как настройка инвентарных файлов, переменных и SSH-доступа к серверам.

7. Обновление формата переменных: Рекомендуется четко оформлять переменные Ansible, чтобы подчеркнуть их важность и предоставить пояснения для каждой используемой переменной, например {{ installapps_apps_list }}.

8. Раздел «Как развернуть»: Добавление более подробного руководства для пользователей, не знакомых с проектом, поможет ускорить процесс знакомства с вашим решением.

9. Использование Ansible Vault: Поскольку в командах используется --ask-vault-pass, полезно предложить объяснение, как настроить и использовать зашифрованные файлы для повышения безопасности.

10. Ссылки на официальную документацию:
    - [Ansible](https://docs.ansible.com/ansible/latest/index.html): Официальная документация Ansible.
    - [Jenkins](https://www.jenkins.io/doc/): Официальная документация Jenkins.
    - [Grafana](https://grafana.com/docs/grafana/latest/): Официальная документация Grafana.
    - [Prometheus](https://prometheus.io/docs/introduction/overview/): Официальная документация Prometheus.