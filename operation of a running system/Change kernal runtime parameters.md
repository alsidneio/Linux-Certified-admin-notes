
- See all kernel runtime parameters run: `sudo systctl -a`
	- net == network related thing 
	- vm == virtual memory 
	- fs == filesystem 


## non- persistent: will revert on restart
- to set a kernel parameter: `sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1`
	- the w flag means to write
- to check a parameter: `sudo sysctl net.ipv6.conf.default.disable_ipv6`
- 
## persistent
- to make a persistent change must create a .conf file in `/etc/sysctl.d/`
	- create a file with the edited parameter 
	- save it 
	- to use the new parameter before the next reboot: 
		- `sudo sysctl -p /etc/sysctl.d/swap-less.conf`

```bash 
# change context of a file 
```sh
sudo chcon -t httpd_sys_content_t /var/index.html
```
```

