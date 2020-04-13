1. $ ansible-playbook inst-httpd.yml
   http://192.168.56.11
2. $ ansible-playbook uninst-httpd.yml
   http://192.168.56.11
   

(venv29) tester@ansible-c:~/ansible/Lab/04.playbooks/01$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/04.playbooks/01$ cat hosts

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

(venv29) tester@ansible-c:~/ansible/Lab/04.playbooks/01$

(venv29) tester@ansible-c:~/ansible/Lab/04.playbooks/01$ cat inst-httpd.yml
---
-
  hosts: web
  become: yes
  tasks:
    -
      name: "ensure nginx is at the latest version"
      apt:
        name: nginx
        state: latest
    -
      name: "ensure ngnix is running"
      service:
        name: nginx
        state: started

(venv29) tester@ansible-c:~/ansible/Lab/04.playbooks/01$ cat uninst-httpd.yml
---
-
  hosts: web
  become: yes
  tasks:
    -
      name: "stop nginx"
      service:
        name: nginx
        state: stopped
    -
      name: "ensure ngnix is not installed"
      apt:
        name: nginx
        state: absent

(venv29) tester@ansible-c:~/ansible/Lab/04.playbooks/01$

