1. APT
# APT: Advanced Packing Tool 의 약자로 Ubuntu나 Debian (계열) linux에서 사용되는 package 관리 툴

$ sudo apt-get update
$ sudo apt install ansible
$ ansible --version

2. APT with Ansible PPA (Personal Package Archive)
# PPA: apt (기본 저장소)를 통해 설치되는 package의 경우, 최신버전이 아닌 케이스가 많기 때문에 PPA을 추가하여 최신 버전을 설치

$ sudo apt-get update
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update # repository add 후 apt update 
$ sudo apt-get install ansible
$ ansible --version

3. VitualEnv with PIP (python package index)

$ sudo apt-get update
$ sudo apt-get install python-minimal virtualenv python-dev build-essential
$ mkdir ansible
$ cd ansible
$ virtualenv venv29
$ source venv29/bin/activate
$ which python # python 설치 위치를 확인
$ which pip
$ pip install ansible
$ which ansible  # ansible이 system path 에 설치되지 않고, venv29 하위에 설치가 된 것을 확인
$ ansible --version
$ pip uninstall ansible # uninstalling ansible
$ deactivate # deactivate a python virtualenv


