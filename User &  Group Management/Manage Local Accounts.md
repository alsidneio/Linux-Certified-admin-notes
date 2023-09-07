```bash 
# add a new user 
sudo useradd john

#look at the skeleton directory used when all users are created
ls -a /etc/skel

# look at the default settings when a user is added 
useradd --defaults
useradd -D

# All settings for account creation are stored
cat /etc/login.defs

# change password for an account 
sudo passwd john 

# Delete an account
# this will delete the john user account and maybe the group 
# johns files and home directory will remain
sudo userdel john 

# remove user home directory along with user 
sudo userdel --remove john

# choosing a different shell for a user at creation
sudo useradd --shell /bin/othershell --home-dir /home/otherdirectory/ john
sudo useradd -s /bin/othershell -d /home/otherdirectory/ john

# all the user creation settings are stored at /etc/passwd
# formatted like the following 
john:x:1001:1001::/home/otherdirectory/:/bin/othershell

usernane: :id number:group-id number:home directory:shell tyep

# manually select an id 
# this will update the group id 
sudo useradd --uid 1100 smith 
sudo useradd - u 1100 smith 

# see what username or group owns directories 
ls -l /home 

# use the -n option to see the numeric number
ls -ln /home

# see current user id 
id 

# see current user 
whoami

# create a system account 
# system account are ment for machines 
sudo useradd --system sysacc

# change user setting after the user has been created
# change home directory
sudo usermod --home /home/diffdirect6ory --move-home john
sudo usermod --d /home/diffdirect6ory -m john

#change user name from john to jane
sudo usermod --login jane john 
sudo usermod -l jane john

# change a users shell
sudo usermod --shell /bin/othershell jane 
sudo usermod -s /bin/othershell jane 

# disables a user login access
sudo usermod --lock jane 
sudo usermod --unlock jane 

# set an account to expire in the futer
# if you want an account to expire immediately set a date in the past 
# to never expire use empty quotes
sudo usermod --expiredate 2021-12-10 jane 
sudo usermod -e 2021-12-10 jane 

## set ann expiration account on the password, to force change of password
# set password change immediately
sudo chage --lastday 0 jane 
sudo chage -d 0 jane 

# undo password
sudo chage -d -1 jane

# set a timeperiod for valid password: 
# to never expire set days to -1
sudo chage -M 30 jane
sudo chage -maxdays 30 jane

# see when a user password expires
sudo chage -l jane

```