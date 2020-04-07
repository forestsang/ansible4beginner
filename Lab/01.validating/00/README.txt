$ ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/00$ ansible all -m ping
node1 | FAILED! => {
    "msg": "to use the 'ssh' connection type with passwords, you must install the sshpass program"
}
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/00$


$ sudo apt-get update

$ sudo apt-get install sshpass

$ ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/00$ ansible all -m ping
node1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/00$
