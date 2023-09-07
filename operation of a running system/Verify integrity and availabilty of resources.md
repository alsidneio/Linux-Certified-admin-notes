Premise: Over time servers will use more and more resources

## Hard drive memory (disk space)
```bash 
# see how much disk space is on your system 
df

# make the output human readable
# ignore file system that says tmepfs 
df -h

# see memory usage of a specific drectory
du -sh

```

## Random Access memory
```bash 
# to see memory usage 
free -h

#
```

## CPU resources 
```bash 
# to see cpu usage
# load averagw: 1 min, 5 min, 15 min
# 1.0 would mean 1 cpu core was fully utilized
uptime 

# see specific cpu on the system 
lscpu

# see information about other components on a system
lscpi


```

## File system Integrity
```bash 
# verify an xfs system 
sudo xfs_repair -v /dev/vdb1

# check and repair an ext4 file system 
sudo fsck.ext4 -v -f -p /dev/vdb2

```

## check processes 
```bash 
# green light means the service is running 
# white light is not running 
systemctl list-dependencies
```