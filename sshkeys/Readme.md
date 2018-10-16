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

Note:
=====

it has private and publickey in https://github.com/settings/keys copy this publickey from /home/.ssh/id_rsa.
and paste in github profile. it works!!!

    /home/arun/.ssh> ls
         id_rsa	 - private key
         authorized_keys2  
         id_rsa.pub - public keys


$
$ cat ~/.ssh/id_rsa.pub
    ssh-keygen 
    
    it generates 
    ssh-add ~/.ssh/id_rsa
