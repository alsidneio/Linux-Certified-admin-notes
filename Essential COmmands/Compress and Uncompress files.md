COmpreession utlities: 
1. gzip 
	1. gunzip
2. bzip2
	1. bunzip
3. xz
	1. u

```zsh
# simple use of the utilities 
gzip file1
bzip2 file2
xz file3

# keep a copy of the imput file 
gzip -k file 

# list contents of a compressed file 
gzip --list file1.zip

# create a zip file 
zip archive.zip file1

# zip a directory
zip -r archive.zip Pictures/

#unzip a zip file 
unzip archive.zip
```

- gzip doesnt compress directories , but ar paired up with tar 
- After you create archive you can use gzip
- but you can also tell tar to archive and compress

```zsh
# Create and compress with tar
	# using gzip
	tar czf archive.tar.gz file1
	
	# using bzip
	tar cjf archive.tar.bz2 file1

	#using xz
	tar cJf archive.tar.xz file1

# tar will automatically pickup the compression utility based on the file ending 
# the a is short for --autocompress
tar caf achrive.xz file1

#extract using a tar command
tar xf arcive.tar.gz file1
```

