(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/02$ cat hosts

web ansible_host=192.168.56.11
db ansible_host=192.168.56.12

(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/02$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/02$


$ ansible web -m ping
$ ansible db -m ping
$ ansible all -m ping
