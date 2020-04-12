(venv29) tester@ansible-c:~/ansible/Lab/03.module$ cat hosts

[control]
control-node ansible_connection=local

[web]
web1 ansible_host=192.168.56.11

[web:vars]
ansible_become=true
ansible_become_pass=welcome1
ansible_port=22

[db]
192.168.56.12

(venv29) tester@ansible-c:~/ansible/Lab/03.module$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/03.module$


- Command modules
 1. $ ansible all -m command -a 'hostname' -o
 2. $ ansible all -a 'hostname' -o # command module의 경우, '-m command'을 명시해주지 않아도 command module이 동작한다.
 
- Files modules
 1. $ ansible all -m file -a 'path=/tmp/x state=touch' -o 
 2. $ ansible all -m file -a 'path=/tmp/x state=file mode=600' -o
 3. $ touch /tmp/copy-me.txt
 4. $ ansible all -m copy -a 'src=/tmp/copy-me.txt dest=/tmp/copy-me.txt'
 5. $ ansible all -m copy -a 'src=/tmp/copy-me.txt dest=/tmp/copy-me.txt'
 # 한번 더 시도한 이유는 output이 초록색 (unchanged) 인 것을 확인 - Idempotency (PPT)
 # 생성한 파일을 삭제
 6. $ ansible all -m file -a 'path=/tmp/copy-me.txt state=absent'
 7. $ ansible all -m file -a 'path=/tmp/x state=absent'
 
- ansible-doc command로 option 확인
 1. $ ansible-doc file
 
 
 
 
