Pre-requisites:
===============

make sure you have /home/arun/.ssh/config using standard template.


STEP 1:
=======


ssh-keygen -o -t rsa -b 4096 -f /home/.ssh/id_rsa

STEP 2:
=======

ssh-keyscan -H 10.1.1.28>> ~ /home/arun/known_hosts

Identity added: /home/arun/.ssh/id_rsa (arundevbox)


    arun@test>ssh-keyscan -H 10.1.1.28 >> ~/.ssh/known_hosts
          # 10.1.1.28:22 SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
          # 10.1.1.28:22 SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
          # 10.1.1.28:22 SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4  

//onlly ip addresss is working
//if i use ssh-keyscan -H arundevbox >> ~/.ssh/known_hosts it is not working.

Step3:
======
still not working remove known_hosts under /home/arun/.ssh/
