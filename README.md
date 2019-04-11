# docker_user

This playbooks adds the AWS EC2 ssh user to docker group. (if group does not existes it creates the docker group)

First Run
------------------------
```
ansible-playbook main.yml -i inventory

PLAY [all] *****************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************
ok: [manager]

TASK [robedevops.docker_user : Ensure group docker exists] *****************************************************************************************************************
changed: [manager]

TASK [robedevops.docker_user : Load user based on OS] **********************************************************************************************************************
ok: [manager] => (item=/home/ansible/.ansible/roles/robedevops.docker_user/vars/CentOS.yml)

TASK [robedevops.docker_user : Add user to docker group] *******************************************************************************************************************
changed: [manager]

PLAY RECAP *****************************************************************************************************************************************************************
manager                    : ok=4    changed=2    unreachable=0    failed=0
```

It shows two changes:
* group is added due there is no docker group
* user is added to docker group


Second Run
--------------------------------
```
ansible-playbook main.yml -i inventory

PLAY [all] *****************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************
ok: [manager]

TASK [robedevops.docker_user : Ensure group docker exists] *****************************************************************************************************************
ok: [manager]

TASK [robedevops.docker_user : Load user based on OS] **********************************************************************************************************************
ok: [manager] => (item=/home/ansible/.ansible/roles/robedevops.docker_user/vars/CentOS.yml)

TASK [robedevops.docker_user : Add user to docker group] *******************************************************************************************************************
ok: [manager]

PLAY RECAP *****************************************************************************************************************************************************************
manager                    : ok=4    changed=0    unreachable=0    failed=0
```

It show there are no new changes.