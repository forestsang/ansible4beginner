$ ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$ ansible all -m ping
The authenticity of host '192.168.56.11 (192.168.56.11)' can't be established.
ECDSA key fingerprint is SHA256:tScQ1m5tBZMkMkqAosLWyZolh02cu1cptnby2wzVa8g.
Are you sure you want to continue connecting (yes/no)? yes
node1 | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: Warning: Permanently added '192.168.56.11' (ECDSA) to the list of known hosts.\r\ntester@192.168.56.11: Permission denied (publickey,password).",
    "unreachable": true
}
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$ ansible all -m ping
node1 | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: tester@192.168.56.11: Permission denied (publickey,password).",
    "unreachable": true
}
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$

위에서 두 번째 동일한 ping 명령을 수행할 때 처음 warning message가 사라진 것을 확인할 수 있다. 이것은 ~/.ssh/know_hosts 파일에 key가 저장되었기 때문이다.

여기서 key 저장 여부를 묻는 단계를 없애고자 한다면, 환경변수 NSIBLE_HOST_KEY_CHECKING=False 을 선언하거나, ansible.cfg 파일에 'host_key_checking = False' 을 추가한다.

$ rm ~/.ssh/known_hosts
$ ANSIBLE_HOST_KEY_CHECKING=False ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$ ansible all -m ping
node1 | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: Warning: Permanently added '192.168.56.11' (ECDSA) to the list of known hosts.\r\ntester@192.168.56.11: Permission denied (publickey,password).",
    "unreachable": true
}
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$ cat ansible.cfg
[defaults]
inventory = hosts
host_key_checking = False
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$

$ rm ~/.ssh/known_hosts
$ ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$ ansible all -m ping
node1 | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: Warning: Permanently added '192.168.56.11' (ECDSA) to the list of known hosts.\r\ntester@192.168.56.11: Permission denied (publickey,password).",
    "unreachable": true
}
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/01$


