arun$>ssh-keygen -R arundevbox


Host arundevbox not found in /home/arundevbox/.ssh/known_hosts


arun$>cat  ~./home/arundevbox/.ssh/known_hosts.

    check entry with 

    arundevbox ecdsa-sha2-nistp256 AAAA+ZbmrHlQrHtjOdHlDDLs39Th731Qx1MX65raZ72Y=


check the pubic key in /home/arundevbox/.ssh/id_rsa.pub matches the publickey in https://github.com/settings/keys 
of your github public profile. yes below accessRights error will come.

Cloning into '/home/arundevbox/repository'...
Permission denied (publickey).
fatal: Could not read from remote repository.
