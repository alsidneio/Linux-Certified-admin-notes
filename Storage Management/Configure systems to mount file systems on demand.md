---
tags:
  - nfs
  - autofs
  - automount
---
ext4
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


Scenario1: 
Tell `autofs` to auto-mount a directory called `/shares`. If this directory does not exist, `autofs` should automatically create it. The `/shares` directory should be defined in a file called `/etc/auto.shares`.


Further, `autofs` should automatically mount a network share `127.0.0.1:/etc` in `/shares/mynetworkshare/` and should show us the contents of `127.0.0.1:/etc` in `/shares/mynetworkshare/` directory.

Solution1:
1. Tell `autofs` that it should mount some NFS share, on demand, this is the first file we need to edit:  
```sh
sudo vi /etc/auto.master
```
  
2. Go to the end of the file and add this line:  
```sh
/shares /etc/auto.shares
```

3. Next, create and edit this file:  
```sh
sudo vi /etc/auto.shares
```
  
4. Here, we tell `autofs` to mount our network share, on demand by adding below given line in it:  
```sh
mynetworkshare -fstype=auto 127.0.0.1:/etc
```

5. With both `/etc/auto.master` and `/etc/auto.shares` edited, it's time to tell `autofs` to pick these changes:  
```sh
sudo systemctl reload autofs
```

6. To verify your changes, you can try to run below given command:  
```sh
ls /shares/mynetworkshare
```

7. You should see the contents of `127.0.0.1:/etc` directory.