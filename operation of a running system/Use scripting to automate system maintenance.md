```zsh
# bash is a shell interpreter
# lets create a script
touch script.sh

# to start a script 
	'#!/bin/bash'
	# log the dat and time the script was last executed
	date >> /tmp/script.log
	cat /proc/version >> /tmp/script.log

 # in ordere to make the script executable
 chmod +x script.sh

# to run the script 
/home/aaron/script/sh ==> ./stript.sh

# archive the /etc/dnf directory 
	'#!/bin/bash'
	tar acf /tmp/archive.tar.gz /etc/dnf

# make it executable
chmod +x archive-dnf.sh

#run it 
./archive-dnf.sh

# improving the backup script using IF and TEST
	#!/bin/bash
	## test -f checks if the file is present
	if test -f /tmp.archive.tar.gz; then 
		mv /tmp.archive.tar.gz /etc/dnf/ /emp/archive.tar.gz.OLD
		tar acf /tmp/archive.tar.gz /etc/dnf/
	else 
		tar acf /tmp/archive.tar.gz /etc/dnf/
	fi

# make it executable
chmod +x archive-dnf-2.sh





```