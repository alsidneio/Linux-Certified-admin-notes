
```bash 
# to see netwrok devices 
ip link 

# to see ip addreses for those devices 
ip addr

# to see the prevouse output with colot 
ip -c addr

# to bring a down interface up 
sudo ip link set dev <interface-name> up

# add an address to an interface 
sudo ip address add 192.168.5.55/24 dev enp0s8

# remove an ip address from a device/interface
sudo ip address delete 192.168.5.55/24 dev enp0s8

```

- the previous commands are not permanent changes, they will be deleted on next restart
- the ip tool is generally used for testing network setting 
```bash 
# to see current network configuration 
netplan get 

# 

```

## Configuring with netplan
- netplan config setting is located at /etc/netplan/
	- the config file is a yaml file

- The following configuration disables automatic ip addresses and allows you to add static ip addresses 

```yaml 
network:
  ethernets: 
    enp0s8: 
	  dhcp4: false
	  dhcp6: false 
	  addresses: 
	    - 10.0.0.9/24
	    - <ipv6 address>
  version: 2 
```

### Configure nameserver with netplan
```yaml
network:
  ethernets: 
    enp0s3: 
	  dhcp4: false
	  dhcp6: false 
	  addresses: 
	    - 10.0.0.9/24
	    - <ipv6 address>
	  nameservers:
	    addresses: 
	      - 8.8.4.4
	      - 8.8.8.8
	  routes: 
	    - to: 192.168.0.0/24
	      via: 10.0.0.100
	    - to: default
	    - via: 10.0.0.1
  version: 2 

```

```bash 
# to apply a current netplan config
sudo netplan apply

# to test netplan configuration
# the try will automatically rollback if changes are not accepted in a certain time 
sudo netplan try

# to choose timeout period for try 
sudo netplan try --timeout 30 
```

### Checking your network configuration 
```bash 
# to list the configured routes 
ip route

# look at the dns resolvers that are configured 
sudo resolvectl status 

# to see just the confugured dns server address
sudo resolvectl dns

# to apply a system wide dns configuration edit the /etc/resolv.conf
# under the [Resolve] section uncomment #DNS
# add your NS addresses seperated by a spacd

# restart the systemd-resolved service 
sudo systemctl restart systemd-resolved.service

# add an ip address of commonly used connections in /etc/hosts file 
#format <ip address> <given_name>

# get hostname information 
hostnamectl



```