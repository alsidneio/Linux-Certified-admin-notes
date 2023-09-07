- the file that defines who can have sudo privilges 
- use the utility `visudo` to edit sudo privileges for users
	- look for the line in the file that refers to "run all/any command"
	- will look like:
		- `%sudo_group_name/username HOST=(RUN_AS_USER) specific_commands`
	- default in most file is: 
		- `%sudo ALL=(ALL) ALL`
- adding a specific user would look like: 
	- `trinity ALL=(ALL) ALL`
- adding a group would look like 
	- `%developers ALL=(ALL) ALL`
- forcing trinity to run sudo as aaron or John users 
	- `trinity All=(aaron,john) ALL`
- we could limit the commands that could be ran eith sudo
- the followiing shows how we can run only ls or bin with sudo
	- `trinity ALL=(ALL) /bin/ls /bin/stat`
- to eliminate the need for a password for a specific user 
	- `trinity ALL= NOPASSWD:ALL`
```bash 
# to open the utility
sudo visudo


```