
Could not open a connection to your authentication agent
=========================================================


STEP 1:
========

   To check ssh agent is started.

command:
=======

  arun@home$ eval `ssh-agent -s`
  arun@home$ssh-add
  Enter passphrase for /home/arun/.ssh/id_rsa: 
  Identity added: /home/arun/.ssh/id_rsa (/home/arun/.ssh/id_rsa)
