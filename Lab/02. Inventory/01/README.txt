(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/01$ cat hosts
# IPAddresses or FQDN

192.168.56.11
192.168.56.12
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/01$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/01$


$ ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/01$ ansible all -m ping
192.168.56.11 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
192.168.56.12 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/01$
