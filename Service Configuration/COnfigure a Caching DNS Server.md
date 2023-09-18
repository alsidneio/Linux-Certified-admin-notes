- A DNS server saves the ip address of a common name 
- caching speeds up calls 
- The Bind utility helps build a local dns cache
	- `sudo dnf install bind bind-utils`
- other utils is : dig 
- Binds configuration can be found: /etc/named.conf

### Listening 
- binds default is configured to listen on port 53 of the localhost
	- `listen-on port 53 { 127.0.0.1; };`
- we can add another ip that bind will listen to: 
	- `listen-on port 53 { 127.0.0.1; 192.168.0.17; };`
- if we want bind to accept connections from any network
	- `listen-on port 53 { any; };`
### Querying 
- by default bind only allows the localhost to query its DNS
	- `allow-query { localhost; };
- you can allow a network to query your local DNS cache by adding to the setting 
	- `allow-query { localhost; 192.168.0.0/24; };
- to allow a query from any network
	- `allow-query { any; };

### Recursion 
- this allows our bind server get dns information from other DNS servers 

```bash 
# start the bind service
sudo systemctl start named.service 

# to ensure the service auto-starts at boot
sudo systemctl enable named.service

# add the DNS to the firewall as a service 
sudo firewall-cmd --add-service=dns

# add the DNS to the firewall as a service, permanently
sudo firewall-cmd --add-service=dns --permanent

# Test if bind is active, use the dig utitlity
# the first time it runs should have a certain tim 
# the subsequent runs should be closer to 0 
dig @127.0.0.1 google.com
dig @localhost google.com

```