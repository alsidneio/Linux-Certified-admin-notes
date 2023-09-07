## Syncing two directories 

```zsh
# syntax
rsync <local-target> <remote-Target>

# synch to a different machine connected via SSH
rsync -a Pictures/ aaron@9.9.9.9:/home/aaron/Pictures/

#rsync will only copy new and changed data 

# rsync can be used update local directories as well

```

## Backup a disk 
- USE the dd command
- dd takes a bit by bit copy, essentially creating an image
- you should unmount the disk before saving the image 
```zsh
sudo dd if=/dev/vda of=diskimage.raw bs=1M status=progress

# restore a disk image, same command in reverse
sudo dd if=diskimage.raw of=/dev/vda bs=1M status=progress
```