/etc/- the file to configure resource limits is `/etc/securtiy/limits.conf`
- the file column format is 
	- #< domain> < type> < item> < value>
		- domain values:
			- * - all users on the system the default 
			- @groupname - refers to a group
			- username
				- a more specific name will override the default
		- type values
			- hard: the absolute number, need admin priveleges to change 
			- soft: a recommended limit. warning, can raise up to the hard limit 
			- -: both a hard and soft limit 
		- item values
			- nproc: number of process that can be opened 
			- fsize: max file size in kb  
			- cpu: limit for cpu time  in minutes 
	- to see more info on configuring resource limits
		- `man limits.conf`
	- login as a different user 
		- `sudo -iu trinity`


- See a users resource limit
	- `ulimit -a`
	- a user vcan only lower these limits