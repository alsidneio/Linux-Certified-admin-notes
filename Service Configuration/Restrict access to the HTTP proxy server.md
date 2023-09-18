## Download & Enable Squid
```bash 
#use squid as the proxy server tool
sudo dnf install squid

# start the service 
sudo systemctl start squid

# enable service to start at boot
sudo systemctl enable squid

# add a firewall entry for squid
sudo firewall-cmd --add-service=squid

# then make it permanent
sudo firewall-cmd --add-service=squid --permanent
```

## Configure Squid 
```vim 
# configuration located at: /etc/squid/squid.conf
# acl == access control list

acl <list_name> <type> <ip in cider> 

# to restrict access to a specific network 
acl localnet src 10.11.12.0/8

# external set of ips that we want to use the proxy
acl external src 203.0.113.0/24

# defining acl by ports 
acl ssl_ports port 443 # 443 is the destination port

# deny request to certain ports 
http_access deny !Safe_ports # deny any connection not in Safe_ports

# when we want to protect applications running on the proxy server 
http_access deny_to_localhost

# giving permissions to the acls 
http_access allow localnet
http_access allow external

# denying access to a specific site/domain 
acl youtube dstdomain .youtube.com 
http_access deny youtube
```

- after configuration reload the service 
- if you want to interupt the service you have to restart the service
- 