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
