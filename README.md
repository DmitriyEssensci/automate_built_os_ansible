# automate_built_os

Repo for project on automate building OS

***Создание роли***  
ansible-galaxy init role_name

***Роли***  
check_system  
grafana  
prometheus  
install_apps  
1c
adduser
jenkins

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
4. grafana - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/grafana.yml   **Возможно потребуется включение VPN для отработки  1.1 задачи ** 

P.S
Если мы ставим мониторинг на клиентские тачки, то следует поставить в значение переменных prometheus_grafana_host_address адрес хоста prometheus

***Prometheus:***  
	http://hostname_ip:9090   

***node_exporter:***   
	http://hostname_ip:9100/metrics   

***grafana:***   
	login/ pass: admin - admin   
	web: http://hostname_ip:3000   
	web_for_prometheus: http://{{ prometheus_grafana_host_address }}:3000/api/prom/push

***jenkins***
	login/ pass: admin - admin   
	web: http://hostname_ip:8080  