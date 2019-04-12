Requirements
------------

For the ubuntu distributions python needs to be installed before start using ansible
* Ubuntu 18-04 LTS - Bionic 
* Ubuntu 16-04 LTS - Xenial

```
apt install python -y
```

Role Variables
--------------
User is defined on variables based on AWS EC2 ssh user. System load the user automatically based on ansible_distribution facts  

```
# for AWS EC2 centos
docker_user: centos
```

```
# for AWS EC2 amazon
docker_user: ec2-user
```

```
# for AWS EC2 ubuntu
docker_user: ubuntu
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters): 

```
- hosts: servers
  roles:
      - { role: robedevops.ansible_docker_user }
```

See example below for CentOS system.
=================

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


License
-------

BSD

Author Information
------------------

Roberto Cardenas Isla - email: rcardenas20@gmail.com