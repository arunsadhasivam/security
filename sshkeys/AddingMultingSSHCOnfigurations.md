Adding multiple SSH Configurations:
===================================

If we need to have 2 config one for local connecting to remote server and one to connect to devbox:
finally we deploy in to jenkins server from our devbox.

Below steps worked!!!!

if you need 2 ssh connections one for github.com and one for virtualbox to install the downloaded github.com

then create 2 ssh rsa publickeys, private keys one for github and one for virtualbox.

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
           
you cannot have the publicy with devbox since you cannot connect to devbox or github without login in to system.
so manually editthe id_dev

both will be home.com since we need one to connect to devbox from localhost change to devbox host or ip.

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACOkbU7wCtMc7OsFhDKxyU5hX6os3tpmSuQ== asadhasivam@home.com

Steps 1: once remote github.com connect
step 2: regenerate the keys in local to devbox (remote ssh) if regenerate command for virtualbox(devbox).
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
