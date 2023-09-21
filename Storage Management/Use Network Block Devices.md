-network block device starts with and n /dev/nbd
## NBD server side  

```bash 
# install 
sudo apt install nbd-server
```

###  NBD config file: /etc/nbd-server/config
```vim 
# comment out user, and group field to run as root
# add `allowlist = true` so that we can see block devices are available

[generic]
#    user = nbd
#    group = nbd
     inludedir = /etc/nbd-server/conf.d
     allowlist = true
     
[partition1]
	exportname = /dev/vda1 
```

- after config change restart the nbd-daemon
	- `sudo sytemctl restart nbd-server`

## NBD client Side 
### config 
```bash
# install nbd client 
sudo apt install ndb-client

# need to plugin an nbd module to the kernel for NBD to work properly 
# thos only loads the module for the current boot 
sudo modprobe nbd

# to load the module at boot we ned to edit the: /etc/modules-load.d/modules.conf
nbd
```

### Managing NBD devices 
```bash
# add the nbd to local device
sudo nbd-client <remote-server-ip> -N <Partion_name_from_server_config>

# mount the nbd to be used 
sudo mount /dev/nbd0 /mnt

# unmount nbd device 
sudo umount /mnt 

# detach nbd device 
sudo nbd-client -d /dev/nbd0

# list available NBDs from 
sudo nbd-client <remote-ip> -l


```
