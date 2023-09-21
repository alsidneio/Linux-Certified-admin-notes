```bash 
# to see all filesystems that are mounted 
findmnt

# to specify the type of file system use the -t option 
findmnt -t xfs,ext4 

# mount options tell you the permissions on the FS

# To mount a read only filesystem 
sudo mount -o ro /dev/vdb2 /mnt 

# Securiiy Mounting 
# noexec option doesnt allow commands to be run from that directory
sudo mount -o ro,noexec,nosuid /dev/vdb2

# remount an already mounted filesystem with diff options 
sudo mount -o remount,rw,noexec,nosuid /dev/vdb2

# for file system dependent option its safer to unmount then mount with options 

## Mount Options at boot time: /etc/fstab





```