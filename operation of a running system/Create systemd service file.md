Scenario: create a service  that will start when the machine boots up and will restart the application if it crashes
- user applicaitons are generally stored in /usr/local/bin
- three sections of a serivce file 
	- unit
	- service
	- install
```bash
# create a script
	#!/bin/bash
	echo "myapp started" | systemd-cat -t Myapp -p info
	sleep 5
	echo "myapp crashed" | systemd-cat -t myapp -p err

# make it executable 
chmod +x /usr/local/bin/myapp.sh

# turn it into a service file 
# use one of the files from the /lib/systemd/system to bootstrap our own system
# you want to place your service file in the /etc/systemd/system/<Name_of_your_service>

[Unit]
Description=My appl8ica
```
