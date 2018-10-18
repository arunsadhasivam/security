To generate ssh keys 
=====================

to connect to git using ssh keys.

  if error is connecting to git "Permissions Denied" issue occur - need public key.
 
 To get access to connect to remote git from local . need to generate public and private key.

   command:
   ========
   
 below command allow from /home dir to request remote connection to github using gitcvs.
 you can ssh keys after login to github = https://github.com/settings/keys
 
   
        c:\arun>ssh-keygen -o -t rsa -b 4096 -f /home/.ssh/id_rsa
        
              Generating public/private rsa key pair.
              Enter passphrase (empty for no passphrase): 
              Enter same passphrase again: 
              Your identification has been saved in /home/.ssh/id_rsa.
              
     
     
    Adding a Key to the SSH Agent
    ===============================

  An ssh agent allows you to avoid typing in the password for your private key. OS X has a built-in ssh agent.
  Add your newly created key with the following command and supply your passphrase when prompted. 
  
  Note: it is important to map instance to key to work correctly.
  
        $ ssh-add ~/.ssh/id_rsa
  
  

 Important:
 ==========
 Afer executing below command it show below result , to confirm mapping done..
 
  $ ssh-add ~/.ssh/id_rsa

 Identity added: ~/.ssh/id_rsa successfully!!!

if " Identity Added sucessfully" message confirms mapping with local to remote established.

Note:
=====

it has private and publickey as below . In https://github.com/settings/keys copy this publickey from /home/.ssh/id_rsa.
and paste in github profile. now it able to handleshake between local and remote git through gitcvs client. it works!!!

    /home/arun/.ssh> ls -l
        -rw------- 1 admin  770 Oct 16 20:26 authorized_keys
        -rw------- 1 admin 770 Oct 16 20:26 authorized_keys2
        -rw------- 1 admin 3434 Oct 16 20:33 id_rsa
        -rw-r--r-- 1  admin  753 Oct 16 20:33 id_rsa.pub
        -rw-r--r-- 1 admin 1106 Oct 16 20:36 known_hosts

$
$ cat ~/.ssh/id_rsa.pub
    ssh-keygen 
    
    it generates 
    ssh-add ~/.ssh/id_rsa
