01. 
 - hosts 파일에 ip addresses 만 정의한 후 ansible ping module로 테스트

02. 
 - hosts 파일에 alias 명, ansible_host=ip-address 적용 후, ansible ping module 테스트
 
03. 
 - hosts 파일에 대표 이름으로 정의하여 테스트 
 - 예: [webservers], [db]

04. 
 - hosts 파일에 ansible_become_user, ansible_become_password을 추가하여 root 권한 획득 예제

05.
 - hosts 파일에 ansible_connection=local을 선언한다. 이는 local connect의 경우, SSH 통신을 하지 않는다.
 - vars 을 이용하여 variable 을 선언하여 특정 서버에 해당 옵션이 적용되도록 정의한다.

06. 
 - hosts 파일에 [all:vars]에 ansible_port=7777 을 작용하여 control node을 제외한 모든 서버들에 대한 ping 테스트가 실패하는 것을 확인

07.
 - hosts 파일에 [web:vars]에 ansible_port을 정의함으로써 [all:vars]에 정의된 ansible_port가 override 되어 정상적으로 ping 성공
 
08.
 - Step 07 inventory 파일을 YAML 형식으로 변경 후, ping 테스트
 
