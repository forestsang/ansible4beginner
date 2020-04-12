(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/08$ cat hosts.yml
---
control:
    hosts:
        control-node:
            ansible_connection: local

web:
    hosts:
        web1:
            ansible_host: 192.168.56.11
    vars:
        ansible_become_user: root
        ansible_become_password: welcome1
        ansible_port: 22

db:
    hosts:
        db1:
            ansible_host: 192.168.56.12

all:
    vars:
        ansible_port: 7777
...
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/08$ cat ansible.cfg
[defaults]
inventory = hosts.yml
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/08$


# Step 07과 동일한 테스트이며, inventory file을 YAML 형식으로 변경하고, ansible.cfg 파일에서 inventory = hosts.yml 로 변경 테스트
$ ansible all -m ping


(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/08$ ansible all -m ping
db1 | UNREACHABLE! => {
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
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/08$
