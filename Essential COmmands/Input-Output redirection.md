- to redirect output use the > symbol, this will overwrite the entire file 
- to append a file use the `>>` to add at the end of the file 

## stdin , stdout, stderr

- stdin == <
- stdout == 1>
- stderr == 2>
```zsh
# redirecting stderr to a file 
2>errors.txt

# sometimes we want to redirect stderr to get rid of some of the messiness
# /dev/null , is like a black hole discard firectory
grep -r  '^The' /etc/ 2>/dev/null

# redirecting stdin & stdout at the same tim 
grep -r  '^The' /etc/  1>>output.txt 2>/dev/null

# redirecting stdin and stdout to the same file 
grep -r  '^The' /etc/ > all_output.txt 2>&1

# Heredoc and here string 
# heredoc, the EOF could be anything 
sort '<<EOF'

# here string
bc <<<1+2+3+4

```

## Piping 
```zsh 
#piping is an output redirect to another command 
grep -v '^#' /etc/login.defs | sort



```
