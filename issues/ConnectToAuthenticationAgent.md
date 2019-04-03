Could not open a connection to your authentication agent.
=========================================================



        ssh-add /home/arun/.ssh/id_rsa.pub

Could not open a connection to your authentication agent.


Solution:
=========
now if you evaluate the command output in your shell, the variable will be set:

      eval $(ssh-agent)

Above command fix the issue by adding the variable in environment.
