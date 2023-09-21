e**NFS:** Network FileSystem Protocol 
- Accessing data on a remote system
## Server Side setup  
```bash 
# install nfs 
sudo apt install nfs-kernel-server

# edite /etc/exports to tell the server which files to share with the network  
# could use cname as in example.com 
# specific ip as in 10.0.0.9
# range of ips: 10.0.16.0/24
<directory/to/share> <ip/hostname_to_share_with(<export_options>)>

# update changes nfs servert 
sudo exportfs -r 

# to see current exports 
sudo exportsfs -v 
```

- Export OPtions
	- Sync: synchronous writes (slow)
	- async: asyncronous writes(fast)
	- no_subtree_check: disables subtree checking 
	- no_root_squash: allows root user to have root priveleges 

## client side setup 
```bash
# install 
sudo apt install nfs-common

# mount a remote nfs server 
sudo mount ip/hostname_of_server:remote.dir/path /local/path/dir

# for automounting  the FS-type == nfs

```