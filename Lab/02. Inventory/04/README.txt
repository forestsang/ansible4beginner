(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/04$ cat hosts

[web]
web1 ansible_host=192.168.56.11 ansible_become_user=root ansible_become_password=welcome1

[db]
192.168.56.12
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/04$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/04$


# web node로 ssh로 connect 후 sudo - root 로 root 권한 획득
# ansible_become_pass 에서 root password가 plain text 로 정의되어 있지만, ansible vault 을 이용하여 암호화할 수 있다.

$ ansible web -m ping

(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/04$ ansible web -m ping
web1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/04$

