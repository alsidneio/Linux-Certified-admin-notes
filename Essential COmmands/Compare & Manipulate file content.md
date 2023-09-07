## View File content

```zsh
# use the cat command for short files 
# use tht tac command for the cat command in reverse

# to see the last lines of the file, use the tail command
#the following will give you the last 20 lines of a file 
tail -n 20 /var/log/dnf.log

# to view the first few lines of the file use the head command
# the head command uses the same options as the tail command
```


## Manipulate file content
```zsh
# Transforming text in a file, use the "sed" command
# many changes in many places

# to precheck the replacement of all occurences of canda to canada
# the preceding s means that the operation is a substitution
# g tells the command to look at every occurence
# the default is to find the first occurence
sed 's/canda/canada/g' userinfo.txt

# to actually change the file you need the -i option which 
# stands for "in-place "
sed -i 's/canda/canada/g' userinfo.txt

# replace every occurence from line a to line b
sed -i 'a,bs/canda/canada/g' userinfo.txt

# Depending on the characters in the string you can use a different delimeter than the '/' to seperate arguments

# the following replaces all occurrences of string `#%$2jh//238720//31223` with `$2//23872031223
sed -i 's~#%$2jh//238720//31223~$2/23872031223~g' data.txt

# extract first column of a file use cut
# -d is the delimeter
# -f is field, field in this case is column
cut -d ' ' -f 1 userinfo.txt

# get unique valuse from file use uniq
uniq countries.txt

#uniq only works if the duplicate values are adjacent
# we must first sort then use uniq. to sort a file: 
sort countries.txt | uniq

```

## Comparing files 
```zsh
# seeing whats different in the file 
diff file1 file2

# to get more context of lines around a file use the -c option
# sidff or diff -y gives you a side by side comparison 
```
