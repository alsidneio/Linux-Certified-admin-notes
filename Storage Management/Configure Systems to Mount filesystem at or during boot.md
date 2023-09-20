/- You can create a file system but you must then mount it for it to be available for use 
- Common directory for mounting is the `/mnt/`
```bash 
# mount a filesystem  to the /mnt/ directory 
sudo mount /dev/vdb1 /mnt/

# to unmount a system
sudo umount /mnt/

```

## automating mounting at boot 
- create the dirextory where you want the filesystem: `mkdir backupSystem`
-  /etc/fstab is the file that file that determines what will be mounted at boot time 
- fstab fields: 
	1. block-device 
	2. mount point 
	3. file system type
	4. mount options 
	5. should dump backup this filesystem 
	6. what happens when errors/corruptions occur 
		1. never scan == (0)
		2. scan  this FS first == (1) 
		3. scan this after the value 1 filesystems have been scanned == (2)

- After edits to fstab be sure to reload the daemon: `sudo systemctl daemon-reload`
- for a swap partition: the mount point is `none` and type is `swap`
- 