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

***Запуск раскатки check_system***  
ansible-playbook --ask-vault-pass --inventory-file inventory/integration/hosts playbooks/check_system.yml
