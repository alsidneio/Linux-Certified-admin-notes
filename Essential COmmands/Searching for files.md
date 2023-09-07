``` zsh
# find /path/to/directory search_parameter
find /bin/ -name file1.txt


# find parameter types
# name: is a case sensitive search 
# -iname: is a case insensitve search 
# -iname "f*" looke for all files starting with and f 

# Find file size 
find /lib64/ -size +10M

# Find file by time edited within the last minute, m stands for modified
# negative looks for changes within that time
# positive looks for changes greater that that interger
# without  the +/- is the exact time 
find /dev/ -mmin -1

# mtime looks in hours 
# the -o option is the or operatior when using find
# when negating, use the -not option & must go before the option to be negated 

#Find files based on permissions
# - would denote the "at least case"
# + would denote an "any" case , files that have any of these permissions
find -perm 664


```