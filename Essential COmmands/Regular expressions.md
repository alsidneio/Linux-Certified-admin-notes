```zsh
# find names that start with sam 
# caret,^,is the begins with operator
grep '^sam' names.txt

# find names that end with sam
# $ is the ends with caret
grep 'sam$' names.txt

# the preiod, . , is an ANY match
# use the \ to escape operators

# the * operator , says match the previous 0 or more times 

# the + operator, says match previous string 1 or more times
# for grep we  must use \ to use the + operator 
# to use extendred regex use egrep or -e option for grep



```

## Extended regular expressions
```zsh
# the -e option on grep or egrep
grep -Er '0+' /etc/ == egrep -r '0+' /etc/

# Brackets looks for a specific number of instances
# the following command looks for at least three zeroes
egrep -r '0{3,}'

# find all strings with a one followed by at most 3 zeros
egrep -r '10{,3}'

# the ? looks for text that 0 or 1 times. 
# use the vertical pipe to match either or 
# the [], operators represent a range 
# use the [^] to negate the pattern


```