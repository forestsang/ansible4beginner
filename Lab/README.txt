1. ansible ad-hoc command에서 root권한으로 작업 '--become'

$ ansible web -m file -a 'path=/var/lib/dpkg/lock state=absent' --become

참고: https://serverfault.com/questions/870951/ansible-adhoc-command-execute-with-sudo
If you have SSH keys shared to your servers in your inventory and you're going to want to sudo to root, you can further reduce the command to this:

$ ansible all -m command -a "docker info" -u myuser --become --ask-become-pass

