- creating filesystems when needed and deleting filesystems as needed
- the utility to accomplish this is: `autofs`
- /etc/auto.master  file format 
	1. mount directory
	2. file that contains the auto mounting options 
		1.  the dirextory that triggers the automount 
		2. fstype
		3. location of nfsshare: ip or hostname 
	3. timeout before auto directory deletion 
- 
```bash
sudo dnf install autofs 
sudo systemctl start autofs 
sudo systemctl enable autofs 

# edit /etc/auto.master to edit the timeout 






# mount a FS on a different directory 
# for this the NFs utility
sudo dnf install nfs-utils 

sudo systemctl start nfs-server
sudo systemctl enable nfs-server





# tell the network what dirextories it should share to the exports file
# do that by editing the /etc/exports file 
sudo vi /etc/exports

# the following line means access to that localhost has read-only acces to the etc directory 
/etc 127.0.0.1(ro)

# reload the nfs-server service to instantiate changes



```

