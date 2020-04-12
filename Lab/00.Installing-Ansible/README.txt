Ansible 설치는 Ubuntu linux 기준이며, 아래 세 가지 방법중에 하나를 택하여 설치할 수 있다. 
개인적으로 가장 좋은 방법이라 생각되는 것은 3번째 VirutalEnv 환경을 구성하여 PIP을 통해 설치하는 방법인데, 이는 하나의 장비에서 python 개발시 서로 다른 버전으로 개발하는 한경을 지원되는 VirtulEnv환경에서 다른 버전이나 환경에 영향을 받지 않고 개발할 수 있는 강점이 있기 때문이다.

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


