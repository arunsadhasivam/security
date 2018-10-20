Pre-requisites:
===============

make sure you have /home/arun/.ssh/config using standard template.

debug:
======

arun$ eval "$(ssh-agent -s)"




STEP 1:
=======


arun$ ssh-keygen -o -t rsa -b 4096 -f /home/.ssh/id_rsa

NOTE:
=====

Also you can get keygen using default(2048) byte.

        arun$ ssh-keygen
        Generating public/private rsa key pair.
        Enter file in which to save the key (/home/arun/.ssh/id_rsa): admin
        Enter passphrase (empty for no passphrase): 
        Enter same passphrase again: 
        Your identification has been saved in admin.
        Your public key has been saved in admin.pub.
        The key fingerprint is:
        SHA256:vJWSBwNHp1lJVgUMzUIxsk022eOIoaoSxyXtNbaXNhs arun@arundevbox.test.com
        The key's randomart image is:
        +---[RSA 2048]----+
        |      ..+o&@oo.  |
        |       o.%+o*    |
        |   .   .*o.+ .   |
        |  . o =..+...    |
        | . + + oS.+      |
        |. o o . E=       |
        | o .   o.+       |
        |. .     .        |
        | .               |
        +----[SHA256]-----+


STEP 2:
=======

arun$ ssh-keyscan -H 10.1.1.28>> ~ /home/arun/known_hosts

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

NOTE:
=====

also if you want use ssh-ad

ssh-add
