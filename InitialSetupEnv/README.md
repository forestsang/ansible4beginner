1. VitualBox Setup

 3개의 virtual machine을 준비한다.
 하나의 서버가 ansible control machine이 되며, 나머지는 (work) node 용도로 사용

2. Network setup
 contorl machine vm network settting에서 bridge network 선택
 
 control machine vm을 start 시킨 후, 아래 package install
 
 2.1 sudo apt install net-tools
 설치 시 lock 관련 파일 에러가 발생하였으며 해당 파일을 'rm /var/lib/dpkg/lockforntend' 로 삭제 후 정상설치
 
 2.2 sudo apt-get install openssh-server
  ssh 통신을 위해 ssh server 설치
  
