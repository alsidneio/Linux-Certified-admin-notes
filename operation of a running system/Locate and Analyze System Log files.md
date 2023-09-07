- rsyslogs  are stored at /var/log
- must have admin access to read rsyslogs
	- use `su` or `sudo --login`
```bash
 # if you dont know which specific logfile to look at grep the entire directory
 # the first line of the grep should let you know which file to look in 
 grep -r '<search_term>' /var/log/

#following log file, live view during debug
tail -F /var/log/secure

#filtering logs created by a certain command 
journalctl /bin/sudo

#filtering rsyslogs to see logs created by a specific service unit
journalctl -u sshd.service

# following in Journalctl
journalctl -F

```


## info, warning, error, critical logs
```bash
# to see the list of priority code names
journalctl -p [tab,tab]

# to see only errors from journalctl
journalctl -p err

# using grep with jounalctl 
journalctl -p info -g '^b'

# filter logs after a certain time 
journalctl -S 02:00

# see logs generated in a time period
journalctl -S 01:00 -U 02:00

# see logs from the current boot
journalctl -b 0

# see logs from previous boot
journalctl -b -1

# who logged in 
last 

# see system users last login
lastlog


```