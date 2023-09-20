i ## CReate  a filesystem
- creating a filesystem is also defined as formatting a filesystem 
- ```
```bash
# create a xfs filesystem 
sudo mkfs.xfs /dev/sdb1



# if you want to label the file system 
sudo mkfs.xfs -L "Backup File System" /dev/sdb1

# define i-node size on the fielsystem 
sudo mkfs.xfs -i size=512 /dev/sdb1

# see xfs utilities 
xfs tab-tab

# create an ext4 file system
sudo mkfd.ext4 /dev/sdb1

# create ext4 with 5k inodes 
sudo mkfs.ext4 -L "BackupVolume" -N 500000 /dev/sdb2

# to modify ext4 fielsystem 
sudo tune2fs -l /dev/sdb2

# modify xfs file systems 
sudo xfs_admin -L "SwapFS" /dev/vdb
```
