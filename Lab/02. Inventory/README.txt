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
