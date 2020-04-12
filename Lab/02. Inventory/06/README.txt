(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/06$ cat hosts

[control]
control-node ansible_connection=local

[web]
web1 ansible_host=192.168.56.11

[web:vars]
ansible_become_user=root
ansible_become_password=welcome1

[db]
192.168.56.12

[all:vars]
ansible_port=7777

(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/06$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/06$


# all로 ping 테스트하는 경우, [all:vars]에 정의된 ansible_port=7777 에 의해 모든 target node에 대한 ping 테스트가 실패하며
# control node의 경우에는 ansible_connection=local로 선언되어 SSH 통신을 하지 않기 때문에 ping 성공
$ ansible all -m ping
