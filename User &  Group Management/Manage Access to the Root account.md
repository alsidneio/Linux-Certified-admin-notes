```bash
# login as root 
sudo --login
sudo -i

# if a user does not have sudo privilege bit knows root passwd
su -
su -l 
su --login 

# when root is locked we can still use 
sudo --login 

# setting a password for root account
sudo passwd root

# unlock a root account 
sudo passwd --unlock root 
sudo passwd -u root

# lock password based access to the root account 
sudo passwd --lock root
sudo passwd -l root



```