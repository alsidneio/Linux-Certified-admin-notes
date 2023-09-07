

```bash
# the command to look at process is 'PS'
# to see all processes running 
ps aux 

# Headings
	#user who is running 
	#process ID == PID
	# %cpu

# items in the brackets are used by the kernal

# to see the continuoyus styate of the system use the top command
# top is default to order by CPU
top

# show process stats by using the process ID
ps u 1

# to see processes started by specific user
ps u -U aaron

# search for process by name 
pgrep -a syslog

#process-niceness, the lower the numver the mvetter t its 
# prpcess inherit the niceness value of the process that called them
# a regular user can only set numbers between 0 -19
# assining lowe nice values
nice -n 11 bash 

# you can use the -l optiion to show nice values, it is under the NI column
ps l 

# to see which processes are parents of a process
ps fax 

# filter output with options with grep
# re assign nice numver as regular user 
sudo renice 12 <PID>


```

## signals 
```bash 
# get a list of uningorable signals 
kill -L


```

## Backgrounding and foregrounding
```bash
# exit a process, ctrl+c

# ctrl+z pauses a process 
# bring paused process back with fg
# to background a process use the & 
# to check for running background jobs  with 'jobs'
# to resume a pasused process use the bg command


# to see currently running/open files 
lsof -p


```