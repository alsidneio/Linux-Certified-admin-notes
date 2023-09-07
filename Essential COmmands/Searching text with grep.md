```
#search through a file
grep -i 'centos' /etc/release.conf

# search for files within a directory and its subdirectory
grep -ir 'centos' /path/to/drirectory

#inbver search mact
grep -iv 'centos ' <somefiel>

#look for a specfic world
grep -wi 'centos' <some_path>

# dont want the entire line? use the -o option
grep -oi 'centos' <some_path>
```