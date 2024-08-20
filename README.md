# automate_built_os

Repo for project on automate building OS

***Создание роли***  
ansible-galaxy init role_name

***Роли***  
add_sys_repo
check_system

***Плейбуки***
add_sys_repo.yml
check_system.yml

***Контуры***  
integration
production

***Группы хостов***  
newmachines -> new_machines:children

***Последовательность запусков ролей***  
1. check_system - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/check_system.yml
2. install_apps - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/install_apps.yml
3. prometheus - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/prometheus.yml
4. grafana - ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/grafana.yml

***Prometheus: ***  
	http://hostname_ip:9090   
***node_exporter: ***   
	http://hostname_ip:9100/metrics   
***grafana: ***   
	admin - admin   
	http://hostname_ip:3000   
