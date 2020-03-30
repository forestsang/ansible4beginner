1. VitualBox Setup

 3개의 virtual machine을 준비한다.
 하나의 서버가 ansible control machine이 되며, 나머지는 (work) node 용도로 사용

2. Network setup
 contorl machine vm network settting에서 bridge network 선택
 
 control machine vm을 start 시킨 후, 아래 package install
 
 2.1 sudo apt install net-tools
 설치 시 lock 관련 파일 에러가 발생하였으며 해당 파일을 'rm /var/lib/dpkg/lockforntend' 로 삭제 후 정상설치
 
 2.2 sudo apt-get install openssh-server
  ssh 통신을 위해 ssh server 설치 후 정상적으로 설치가 되었는지 확인
  
  tester@tester-VB:~$ service ssh status
● ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2020-03-30 15:19:46 KST; 4min 16s ago
 Main PID: 4532 (sshd)
    Tasks: 1 (limit: 2339)
   CGroup: /system.slice/ssh.service
           └─4532 /usr/sbin/sshd -D

 3월 30 15:19:46 tester-VB systemd[1]: Starting OpenBSD Secure Shell server...
 3월 30 15:19:46 tester-VB sshd[4532]: Server listening on 0.0.0.0 port 22.
 3월 30 15:19:46 tester-VB sshd[4532]: Server listening on :: port 22.
 3월 30 15:19:46 tester-VB systemd[1]: Started OpenBSD Secure Shell server.
 3월 30 15:21:20 tester-VB sshd[4653]: Accepted password for tester from 192.168.219.173 port 53556 ssh2
 3월 30 15:21:20 tester-VB sshd[4653]: pam_unix(sshd:session): session opened for user tester by (uid=0)
 3월 30 15:21:21 tester-VB sshd[4655]: Accepted password for tester from 192.168.219.173 port 53557 ssh2
 3월 30 15:21:21 tester-VB sshd[4655]: pam_unix(sshd:session): session opened for user tester by (uid=0)




  
