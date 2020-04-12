(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/03$ cat hosts

[webservers]
192.168.56.11
192.168.56.21
192.168.56.31
192.168.56.41
192.168.56.51

[db]
192.168.56.12
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/03$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/02.inventory/03$

$ ansible webservers -m ping
$ ansible db -m ping

# '-o' 옵션을 추가하면 결과를 한 줄로 보여준다.
$ ansible all -m ping -o 
