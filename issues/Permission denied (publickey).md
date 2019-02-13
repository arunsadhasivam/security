Error:
======

Permission denied (publickey).
Please make sure you have the correct access rights
and the repository exists.



check:
======

check the permission /users/.ssh/ 

give chmod 777 .ssh - to give full permission.


or

ssh-add /users/arun/.ssh/id_rsa.

then try it should work.

