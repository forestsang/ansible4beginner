$ ssh-keygen

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/02$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/tester/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/tester/.ssh/id_rsa.
Your public key has been saved in /home/tester/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:cno6RnSMRanlJjDsy6i8c+tZMAIwxDDpW8GWe9k2Re8 tester@ansible-c
The key's randomart image is:
+---[RSA 2048]----+
|Oo...  .oo       |
|o+ =+   +..      |
|o ..oooB.  .     |
|.. o.o=+= .      |
| .o=.oo+S  E     |
| .o = .+         |
|..   o. .        |
|.o .o oo         |
| .=+....         |
+----[SHA256]-----+
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/02$

$ ssh-copy-id 192.168.56.11

/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/tester/.ssh/id_rsa.pub"
The authenticity of host '192.168.56.11 (192.168.56.11)' can't be established.
ECDSA key fingerprint is SHA256:tScQ1m5tBZMkMkqAosLWyZolh02cu1cptnby2wzVa8g.
Are you sure you want to continue connecting (yes/no)? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
tester@192.168.56.11's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh '192.168.56.11'"
and check to make sure that only the key(s) you wanted were added.

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/02$


$ ssh 192.168.56.11

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/02$ ssh 192.168.56.11
Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 4.18.0-18-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


 * Canonical Livepatch is available for installation.
   - Reduce system reboots and improve kernel security. Activate at:
     https://ubuntu.com/livepatch

433 packages can be updated.
260 updates are security updates.

Your Hardware Enablement Stack (HWE) is supported until April 2023.
Last login: Tue Apr  7 23:00:23 2020 from 192.168.56.10
tester@ansible-node1:~$

$ ansible all -m ping

(venv29) tester@ansible-c:~/ansible/Lab/01.validating/02$ ansible all -m ping
node1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
(venv29) tester@ansible-c:~/ansible/Lab/01.validating/02$



