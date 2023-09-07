
Step1: Archive
Step2: Compress
Step3: Store the compressed archive

TAR == Tape Archive
tar is a packer and unpacker

## Packing files and directories
```zsh
# the following commands porduce the same result
tar --list --file archive.tar
tar -tf archive.tar
tar tf archive.tar

# alsways ad f at the end of the options

# create a tar files
tar --create --file archive.tar file1
tar cf archive.tar file1

#Add a file to the archive 
tar --append --file archive.tar file2 
tar rf archive.tar file2

#create an archive of a directory
# the path given in a tar file will have the same structure packed up
tar --create --file archive.tar Pictures/

# look at file path before extracting a tarball
tar --list --file archive.tar
tar tf archive.tar

# extract a tarball 
tar --extract --file archive.tar
tar xf archive.tar

# extract to specific directory 
tar --extract --file archive.tar --directory /tmp/
tar xf archive.tar -C /tmp/

```

## Gotchas 
- if you see a `tar: Removing leading '/' from member names`
	- use the -P option