(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/07$ cat hosts

[control]
control-node ansible_connection=local

[web]
web1 ansible_host=192.168.56.11

[web:vars]
ansible_become_user=root
ansible_become_password=welcome1
ansible_port=22

[db]
192.168.56.12

[all:vars]
ansible_port=7777

(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/07$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/07$

# 아래 명령어로 [web:vars]에 정의된 ansible_port 값이 [all:vars]에 정의된 동일한 값보다 우선되어 정상적으로 web의 경우 ping이 됨을 알 수 있다.
$ ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/07$ ansible all -m ping
192.168.56.12 | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: ssh: connect to host 192.168.56.12 port 7777: Connection refused",
    "unreachable": true
}
[DEPRECATION WARNING]: Distribution Ubuntu 18.04 on host control-node should use /usr/bin/python3, but is using /usr/bin/python for
 backward compatibility with prior Ansible releases. A future Ansible release will default to using the discovered platform python
for this host. See https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information. This
feature will be removed in version 2.12. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
control-node | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
web1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/07$
