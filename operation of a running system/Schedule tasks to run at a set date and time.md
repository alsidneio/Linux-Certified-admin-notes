## Scheduling Jobs with cron 

- system wide coront table is located at /etc/crontab
- format of a cron job from left to right
	- <minute (0-59)> 
	- <hour (0-23)> 
	- < day (1-31)> 
	- < Month >
		- (1-12)
		- jan,feb.mar.apr,may,jun,jul,aug,sep,oct,nov,d*0
	- < day-of-week >
		- valid types for day of the week
			-  (0-6), (sunday=0 or 7)
			- sun,mon,tue,wed,thu,fri,sat 
	- < user-name> 
	- < command-to-be-executed>

### Cron special characters
- * = = match all possible values (i.e, every hour)
- , == match this specific list of values
- - == match the range of values
- / == specific steps (*/4) is every four hours

### special Cron directories 
- daily = `/etc/cron.daily`
- hourly = `/etc/cron.hourly`
- monthly = `/etc/cron.monthly`
- weekly = `/etc/cron.weekly`

- cronjob shellscripts should have no extension
	- the script should be readable and executable

```bash 
# find the full path of a command use `which`
# always use the full command path in a cron job

# Edit the current users cron page
crontab -e

# to create a file everyday at 6:35 am 
35 6 * * * /usr/bin/touch test_passed

# to create a file every sunday at 3 am 
0 3 * * 7 /usr/bin/touch test_passed

0 3 * * 0 /usr/bin/touch test_passed

#  run every month on the 15th at 3am 
0 3 

# see crontab of current user 
crontab -l 

# see crontab of root user 
sudo crontab -l

# see crontab of another user 
sudo crontab -e -u jane_test

# remove the current user crontab
crontab -r 

# remove crontab of another user
sudo crontab -r -u jane


```
## Anacron Jobs: dont care when the job runs 

- system wide anacron jobs are stored at `sudo vim /etc/anacrontab`
- syntax: 
		-  < period in days> < delay in minuttes> < job identifier> < command>. 

```bash 
# want to run a job every 3 days called test job 
3 10 test_job /usr/bin/touch  /root/anacreon_creation

# want to run every 7 days 
7 10 test_job /usr/bin/touch  /root/anacreon_creation
@weekly 10 test_job /usr/bin/touch  /root/anacreon_creation

#want it to run monthy
@monthly 10 test_job /usr/bin/touch  /root/anacreon_creation

# you can test your script with 
anacrontab -T


```
## Scheduling jobs with At
- with at commmand we just specify the time we want the command to run
- syntax: 
```bash 
# we want the job to run at 3 pm
at 15:00
	at> /usr/bin/touch file_to_be_created

# run a job at a specific date 
at 'August 20 2022'

# run a job at a specific time on the date 
at '2:30 August 20 2022'

# run a command at a later time 
at 'now + 3 hours '
at 'now + 3 days '
at 'now + 3 weeks '
at 'now + 3 months'

# to see the queue of scheduled jobs 
atq

# to see what a job contains 
atq -c 

# to remove a command 
atrm <jobID>

```