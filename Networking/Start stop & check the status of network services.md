 :# utilities to check network services 
```bash 
# see current servies and networking info 
# Options explanation
	# -l = service that is listening 
	# -t = will list only TCP connections
	# -u = will list only UDP connections 
	# -n = will give the numeric port values 
	# -p = show associated processes
	
sudo ss -ltunp 

# netstat uses the same options but is the oldeer tool 


```

- 127.0.0.1 is the localhost , so is only listening for connections on the host machine
- 0.0.0.0 is the local network: so listening for any connections on the local network
-
- from this output you can:
	- get the service thats running 
		- use the systemctl to see info about the service
	- get the PID 
		- use ps command to get more info about the process
		- use lsof to see which files the process have open 
	- 