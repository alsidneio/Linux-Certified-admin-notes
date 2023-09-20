---
tags:
  - swap
  - partitions
  - swapon
  - dd
---

swap disk is where the host can offload some  memory , temporarily 
## create swap from disk partitionon
```bash 
# see current swap config
swapon --show

# look at partitions available 
lsblk

# create a swap partition 
sudo mkswap /dev/vdb3

# set the partition as a swap disk 
sudo swapon --verbose /dev/vdb3

# stop using a filesystem as swap 
sudo swapoff /dev/vdb3

```

## Create swap from file 
```bash 
# create a file with the amount of 0s for the memory you want.
# use the status=progress command to see the progress
sudo dd if=/dev/zero of=/swap bs=1M count=128 status=progress

# the swap file shoul be read and write only to the user 
sudo chmod 600 /swap

# set the file as the swap
sudo mkswap /swap

# make file the active /swap
sudo swapon --verbose /swap

# confirm it is listed as the swap 
swapon --show
wa[]
```