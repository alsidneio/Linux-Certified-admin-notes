- With the ssh daemon running 
- the config file for sshd is : `/etc/ssh/sshd_config`
	- you can use man to understand differnt params for this 
- the ssh client file is located: `/etc/ssh/ssh_config`

## Server Side Config
### Important settings  
- `Port` : the port on which ssh connections are accepted , default is generally 22. 
- `AddressFamily`: specifies the address family which should be used by sshd
	- any == ipv4 or ipv6
	- inet == ipv4 only
	- inet6 == ipv6 only
- `PasswordAuthentication`: specifies if you need a password to authenticate, default is yes
	- if you change this to no, then users can only login with keys
	- if you set to no, except for a specific user 
```vim
PasswordAuthentication no
Match User aaron
	PasswordAuthentication yes
```

- `ListenAddress` : specifies which network to listen to, default is all @ `0.0.0.0`
- `PermitRootLogin`: specifies if you can login as root. Default is yes. 
- `X11Forwarding`: if we get a graphical interface when trying to log in 
- everytime we change the config file we have to reload with 

## Client Side Config
- look at options for client side config `man ssh_config`
- get ip address of the machine with `ip a`
- create a new file @ `.ssh/config` to look like
```vim 
Host Ubuntu
	HostName <some_ip>
	Port 22
	User aaron
```
- change the permission to chmod 600
	- changing this because the ssh daemon requires that the dile shouldnt be readable to anyone else 
-
### Generating keys for login 
- use `ssh-keygen` it will create a private key and a public key and they will be stored in the .ssh folder 
- you must give the server the public key for authentication
	- `ssh-copy-id user@<host_server_ip>`
		- the pub file would be stored at `.ssh/authorized_key` on the server directory
	- if cant use `ssh-copy` you have to add them manually
			- copy the pub key to the `authorized_keys` file 
			- change the permissions to 600, `chmod 600`
			- 