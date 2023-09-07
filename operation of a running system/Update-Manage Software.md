- updating helps prevent exploitation of known security vulnerabilities 
```bash 
#check upgradable packages

#upate all packages 

#
```

## Managing Software 
```bash 
# see default repsotories in APT
ls -l /etc/apt

# list pack repo including web address 
apt show

# optional repositories for unbuntu 

# enable optional repository

# disable optional repository 

# search repo for keyword
apt search <search string> 
apt search python

# get more info about a  package 
apt-cache show <package_name>
apt-cache show gcc

# update a repository
sudo apt-get update

# update local packages
sudo apt-get upgrade

# install a package 
sudo apt-get install grafana

# remove a package 
sudo apt-get remove <package>

# purging packages
sudo apt-get purge <package>

# autouninstall dependencies 
sudo apt-get autoremove <package>(option)
```