```bash 
# SE linux context label
user: role: type: level
unconfide_u:pbject_r:user_home_t:s0


# SEL Logic
	# is the user valid 
	# does the user have the proper role 
	# can the role access the type/domain
# if any part of this logic fails then its an automatic reject

# change context of a file 
sudo chcon -t httpd_sys_content_t /var/index.html

 

```

- SEL Logic
		- is the user valid 
		- does the user have the proper role 
		- can the role access the type/domain
if any part of this logic fails then its an automatic reject

```bash
# to see current user security context
id -Z

# to see mapping 
sudo semanage login -l 

# to see mapping of all users on the system
sudo semanage user -l

# to see if selinux is enabled and enforcing 
# Enforcing means its actively applying rules
# Permissive means it logging what permissions should be applied 
# Disabled, its off
getenforce

# set SELinux to permissive
```sh
sudo setenforce 0
```



```