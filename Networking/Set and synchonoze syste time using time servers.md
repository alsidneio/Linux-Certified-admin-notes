chron- the service that controls time is chronyd.service 

```bash 
# to ensure the service is running 
systemctl status chronyd.service

# check if system clock is synchronixed and actuve 
timecdatetl

# to enable chronyd if not installed by default
sudo timedatectl set-timezone <region>/city

# to list accepted timezones
timedatectl list-timezones 

# install chronyd 
sudo apt-get install

# start the chronyd service 
sudo systemctl start chronyd.service 

# set to start at boot time 
sudo systemctl enable chronyd.service 

# use timedatectl to see if sycnhronized is yes 
# if not you can manually set ntp to true 
sudo timedatectl set-ntp true

```