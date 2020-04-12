(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/05$ cat hosts

[control]
control-node ansible_connection=local

[web]
web1 ansible_host=192.168.56.11

[web:vars]
ansible_become_user=root
ansible_become_password=welcome1

[db]
192.168.56.12

[db:vars]
ansible_port=7777

(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/05$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/05$


# 아래 web에 대한 ping으로 web:vars에 선언한 variables가 web에서 사용되어 sudo - root로 권한을 획득
$ ansible web -m ping

# 아래 db에 대한 ping으로 [db:vars]에 선언된 ansible_port=7777 이 적용되어 connection이 failed 되는 것을 확인할 수 있다.
$ ansible db -m ping

# 아래 명령어로 db node 제외한 서버들에 대한 ping이 정상적으로 되는 것을 확인한다.
$ ansible all -m ping



