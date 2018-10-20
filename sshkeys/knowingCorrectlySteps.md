Pre-requisites:
===============

make sure you have /home/arun/.ssh/config using standard template.




debug:
======

arun$ eval "$(ssh-agent -s)"

arun$ ssh -v arundevbox

        debug1: Offering public key: RSA SHA256:yJv1nj6k1z9YNm478AjW1iCNVONMZp+bYDunjXtDuy8 arundevbox
        debug1: Authentications that can continue: publickey
        debug1: Offering public key: RSA SHA256:60giddHdpYJ4HcjSknasKk0nCL7ET/x/UMQJS5uexMs arundevbox
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
//if i use ssh-keyscan -H arundevbox >> ~/.ssh/known_hosts   also works

        asadhasivam$ ssh-keyscan -H arundevbox >> /home/arun/.ssh/known_hosts
        # asadhasivam-dbx:22 SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
        # asadhasivam-dbx:22 SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
        # asadhasivam-dbx:22 SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4

Note:
=====

make sure space between arundevbox >> /home/arun/.ssh/known_hosts

Step3:
======
still not working remove known_hosts under /home/arun/.ssh/

NOTE:
=====

also if you want use ssh-ad

ssh-add


Available commands:
====================

        ssh          ssh-agent    ssh-keygen   sshd         
        ssh-add      ssh-copy-id  ssh-keyscan  

ssh-add
=======

ssh-add - adds private key identities to the authentication agent  


parameters:
============
        -L-
                Lists public key parameters of all identities currently represented by the agent.
        -l
                Lists fingerprints of all identities currently represented by the agent.
                
 E.g:
 ====

arun$ssh-add -L

                ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDdL+nM3ZtkbJ7CcccroFjTaAaAwrEay/OvOxW0xknHvoLKlfoz1F9TBQnIduGwVhpPZ9U/lBNuep14fsJ72pLTVZ1q0wHCQOuHzu7iYN7AtpnI9TfGQaz4Ho4y8WRcjKvGBTMjRlCNGTPvgnu/0Kloa+C+3qJe42TbzNW1uySz/iXJNhCFEl/3Jl/ThBooB2jCL1hI6Ig0EQwuT0eahElLQW5kn53pq/pCOLety95SfPEPcP9HWXsNNLhaODRSEbEIwWOjuwlJYt16CWV8kOat1Jar13G6JyKA1iQF4ncy4ad+hXxp1U7u/ZBnkLZ24VOqGq273EjrMTPQzWj11VA/UuRRKCrgxeQcmLPwCvakjZhpeks2tPfWT0ds/9VKqDLtbrMtrywUPeRGl7u77pYZj3WHBgPU1HpIn4EcERJ5WghGCzDjDakQtwLx/3YR8Jv7FJ0/Knw0c6uyeTeeFDqwW6cMUCm2MxYHeHngXKZ15pTGLqygmymvh5e9mil0vP3mLL80YM7cDzuiHppCOay938f8NYBx0rH6nTrCeTVPfH7wee0tY6CrbErLHeVxTA37REEVUAS0DZvl2TxPdAPJNYVVQ/EKB7CUjUlSe8rD7Io/HfD1qwCnLP0RZGINnnFEGWgFD0wORIdIwR+NvBD8UUnxoKA0Fgdl4vBNPfEe5w== arundevbox@localhost

