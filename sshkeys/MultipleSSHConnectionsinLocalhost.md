Adding multiple SSH Configurations:
===================================

If we need to have 2 config one for local connecting to github  and one to connect to devbox:
finally we deploy in to devbox to test.

Below steps worked!!!!

if you need 2 ssh connections one for github.com  and one for virtualbox to install the downloaded github.com

then create 2 ssh rsa publickeys, private keys one for github handshake with localhost and one for virtualbox to localhost.


1) handhsake between local -> github
    internet connection in your local to talk to github.com remote server with exchage of public and
    private keys
    
2) handshake between local -> devbox - need to generate public keys in devbox and then use this to checkout
code.

check any way to generate public keys for the virutalbox in local.

if internet connection exists we can connect form localhost to github.com but for virtualbox we need the
virtual box public key generated along with private key to make it work.

copy the 2 public keys of github.com and public keys of devbox where we deploy our code and build 
in to jenkins server where all code deployed by maven.
https://github.com/settings/keys


create 2 rsa publickeys:
========================

arun# ssh-keygen -o -t rsa -b 4096 -f ~/.ssh/id_rsa

arun# ssh-keygen -o -t rsa -b 4096 -f ~/.ssh/id_devbox_rsa

localhost has below:
====================

NOTE:
=====

see no change in localhost devbox private key only public key changed from devbox.

        arun$ ls -l
        -rw-------  1 arun  HOME\Domain Users  3479 Oct 19 19:12 id_devbox_rsa
        -rw-r--r--  1 arun  HOME\Domain Users   753 Oct 19 19:37 id_devbox_rsa.pub
        -rw-------  1 arun  HOME\Domain Users  3479 Oct 19 18:50 id_rsa
        -rw-r--r--  1 arun  HOME\Domain Users   770 Oct 19 18:50 id_rsa.pub
        -rw-r--r--  1 arun  HOME\Domain Users   607 Oct 19 19:35 known_hosts



NOTE:
======

generate the id_rsa.pub keys from devbox and copy to this file.

like it should be



 asadhasivam$ cat id_devbox_rsa.pub // copied from devbox after generation of keys.
 
     ssh-rsa SX7J464aDLxfexX6s3cevc3w/HmFH/88IKIPTYNI67O2tRnIC2I07xff7oaravcqPA
     llA/qiC7dOASx0ODSTvdOWzbb3q9SZx54kla9l6sajk6XrGtfh8cBTLJ8843YXJ
     y1n2IHhbgkQmtFoJREP1etdiE0w== arun@arundevbox.

 IMPORTANT:
 ==========
   
   first generate private and public keys and then change only public key copied from
   devbox actual server. just ignore private key . cat id_devbox_rsa(privatekey) just dont change.
 
 asadhasivam$ cat id_rsa.pub
 
     ssh-rsa AAAAB3NzaC1yc2EA/HmFH/88IKIPTYNI67O2tRnIC2I07xff7oaravcqPA
     llA/qiC7dOASx0ODSTvdOWzbb3q9SZx54kla9l6sajk6XrGtfh8cBTLJ8843YXJ
     y1n2IHhbgkQmtFoJREP1etdiE0w== arun@localhost.com



  

Add generated private keys to ssh Agent:
========================================

    private key to connect to remote server github.com:
    ===================================================

             arun#  ssh-add /home/arun/.ssh/id_sa
            Enter passphrase for /home/arun/.ssh/id_rsa: 
            Identity added: /home/arun/.ssh/id_rsa (arundevbox@github.com)

        

    private key to connect to remote devbox to donwload github code:
    =================================================================
        
        arun#  ssh-add /home/arun/.ssh/id_devbox_rsa
        Enter passphrase for /home/arun/.ssh/id_devbox_rsa: 
        Identity added: /home/arun/.ssh/id_devbox_rsa (arundevbox@home.com)
           

Steps 1: generate public,private key for local-github -internet
step 2: regenerate the private,publickey for remote devbox.
Step 3: generate the public key and private key for remote devbox and copy the public key from devbox 
to local system. igore private key.
i.e copy public key generated from devbox and copy to local /home/arun/.ssh/id_dev_rsa.pub 

STEP 4: don't distrub the local /home/arun/.ssh/id_devbox_rsa private key.

since we configure 2 ssh-add (private keys) to connect to agent it wont collapse else it always mingle 
if we have one ssh public , private keys.
i.e if we have one ssh keys(public  , private) then first time you connect to github.com it binds, next when you
try to connect to devbox already agent bind to github.com remote so it wont connects. says 

    "fatal: Could not read from remote repository.
    Please make sure you have the correct access rights


NOTE:
====

if not working try rm known-hosts in /home/ssh/known_hosts.
    "
