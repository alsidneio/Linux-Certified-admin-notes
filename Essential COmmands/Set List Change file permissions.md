```zsh
# change group of a directory
# chgrp group_name file/directory
chgrp wheel family_dog.jpg

#see which groups the current user belongs to 
groups

# change the user owener of a file/directory 
# sudo chown over_name file/directory
sudo chown jane family_dog.jpg

# When you run ls -l there is a format: 
# <file_type><user_permission><group_permission><world_permission>

# changee permission
# chmod permissions file/driectory
# add a write permission for the user owner 
chmod u+w family_dog.jpg
```

| File Type        | Identifier |
| ---------------- | ---------- |
| Directory        | d          |
| regular file     | -          |
| character device | c          |
| link             | l          |
| socket file      | s          |
| pipe             | p          |
| block device     | b          |
|                  |            |


- read, write, execute on a directory will apply to files in a directory
- 