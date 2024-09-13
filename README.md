# automate_built_os

Repo for project on automate building OS

***Создание роли***  
ansible-galaxy init role_name

***Роли***  
check_system
grafana
install_apps
prometheus

***Плейбуки***  
check_system.yml
grafana.yml
install_apps.yml
prometheus.yml

***Контуры***  
integration
production

***Группы хостов***  
newmachines -> new_machines:children

***Последовательность запуска ролей***  
1. check_system - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/check_system.yml
2. install_apps - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/install_apps.yml
3. prometheus - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/prometheus.yml
4. grafana - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/grafana.yml   ***Возможно потребуется включение VPN для отработки  1.1 задачи ***  

***Prometheus:***  
	http://hostname_ip:9090   

***node_exporter:***   
	http://hostname_ip:9100/metrics   

***grafana:***   
	login/ pass: admin - admin   
	web: http://hostname_ip:3000   
	web_for_prometheus: http://{{ prometheus_grafana_host_address }}:3000/api/prom/push

