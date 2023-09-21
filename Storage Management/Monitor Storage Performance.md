- Monitor CPU and MEm
	- `top , htop`
- Monitor disk storage: iostat, pidstat from the sysstat package 
- iostat gives us metrics from bootup 
	- it takes the average usage over total time since boot 
	- tps = transfers per second 
	- kB_read/s == kilobytes read per second 
	- kB_wrtn/s == kilobytes written per socond 
	- kB_dscd/s == kbs discarded due to errors
- `iostat < num in second>`
	- `iostat 10 ` : will keep giving stats from the last 10 second 
- `io stat -d`:  gets rid of the cpu information 
- `iostat -h`:  outputs the info in a human readable form

## Demo

```bash 
# installation 
sudo apt install sysstat

# create a process to constanttly write to a process 
dd if=/dev/zero of=DELETEME bs=1 count=1000000 oflag=dsync &

# run iostat writes and reads
# to see partitions with iostat
iostat -p ALL

# to see partitions for a specific storage device 
iostat -p vda

# to see which processes use pidstat
# to see associated devices run
pidstat -d --human

# kill a process 
kill PID

# force kill a process
kill -9 PID 

```