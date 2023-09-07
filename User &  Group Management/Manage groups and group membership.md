- groups give user profile access == roles 
- primary group is the login group
	- when a proceess run it runs with the permissions of that user 
```bash 
# create a group 
sudo groupadd developers

# add john to the group with the gpasswd 
sudo gpasswd --add john developers
sudo gpasswd -a john developers

# see groups that a user is apart of 
groups john

#remove a user from the group 
sudo gpasswd -d john developers 
sudo gpasswd --delete john developers

# change a users primary group 
sudo usermod -g developers john 
sudo usermod --gid developers john 

# rename a group
sudo groupmod --new-name programmers developrs
sudo groupmod -n programmers developrs

#delte a group sudo groupdel programmers 
# a group cannot be deleted if its someones primary group 
sudo groupdel programmers

```