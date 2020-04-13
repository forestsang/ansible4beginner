$ ansible-playbook setup-simple-web.yml
 
 
 - python dependency package 설치
 - pymysql을 pip 으로 설치
 - MySQL 설치 by apt
 - database 시작
 - application database 생성
 - database user 생성
 - sample data용 file copy
 - sample data을 application database에 import
 - python flask 설치
 - python sample program 복사
 - Web server 시작
 - 브라우저를 통해 확인
  * http://192.168.56.11:5001/
  * http://192.168.56.11:5001/how are you
  * http://192.168.56.11:5001/read from database
