---
tags:
  - lsblk
  - fdisk
  - cfdisk
  - blockstorage
---


Partioning: dividing a hard drive to host two different filesystems 
- all disks are located in the `/dev/` directory
```bash
# to see partitions on a linux system 
# the ones with 'part' or partitons
lsblk

# see partitions on a particular disk 
# sectors 
sudo fdisk --list /dev/sda 

# c disk is an interactive tool for partitioning 
# use gpt for most modern systems 
sudo cfdisk /dev/sdb



```