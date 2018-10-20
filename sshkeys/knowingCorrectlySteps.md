Pre-requisites:
===============

make sure you have /home/arun/.ssh/config using standard template.

debug:
======

arun$ eval "$(ssh-agent -s)"

arun$ ssh -v arundevbox

        debug1: Offering public key: RSA SHA256:yJv1nj6k1z9YNm478AjW1iCNVONMZp+bYDunjXtDuy8 asadhasivam@asadhasivam-dbx
        debug1: Authentications that can continue: publickey
        debug1: Offering public key: RSA SHA256:60giddHdpYJ4HcjSknasKk0nCL7ET/x/UMQJS5uexMs asadhasivam@asadhasivam-mba.corp.dropbox.com
        debug1: Authentications that can continue: publickey
        debug1: Trying private key: /home/arun/.ssh/id_rsa
        debug1: Trying private key: /home/arun/.ssh/id_dsa
        debug1: Trying private key: home/arun/.ssh/id_ecdsa
        debug1: Trying private key: /home/arun/id_ed25519
        
To get more verbose:
====================

arun$ ssh -v arundevbox

arun$ ssh -vv arundevbox






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
