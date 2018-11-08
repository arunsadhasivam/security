To check login with particular ssh files
=========================================


if you have multiple .ssh files and you want to confirm whether any issue with particular .ssh files.

    arun$>pwd
    /user/arun/.ssh

    arun$.ssh>  ls -l

    id_rsa.pub
    id_rsa
    id_test.pub
    id_test


To check connectivity with  specific .ssh file  use below command.

    ssh -i ~/.ssh/id_rsa.pub arun@devbox

     Last login: Wed Nov  7 16:23:57 2018 from 10.16.47.231
