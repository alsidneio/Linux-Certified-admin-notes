goal : add a zone using bind for example.com 
- edit the bind conf file located at /etc/named.conf 
```vim
" add a zone config to the file 
zone "example.com" IN {
		type master;
		file "example.come.zone"
};

```

- TYPE master is the source of truth for example.com
- FILE is the file that the zone data can be found 

- bind keeps zone, log, and variable data in `/var/named`
	- copy named.localhost  using : `sudo cp --preserve=ownership /var/named/named.localhost /var/named/example.com.zone`

```vim 
TTL 1H 
@ IN SOA  @ administrator.example.com. (
								0  ; serial 
							    1D ; refresh 
								1H ; retry
								1W ; expire
								3H ; minimum
)

@            NS       ns1.example.com.
@            NS       ns2.example.com.
ns1          A        10.11.12.9
ns2          A        10.11.12.10
@            A        203.0.113.15
www          CNAME    203.0.113.15
example.com. mx 10    mail.example.com.
             mx 20    mail.example.com.
mail         A        203.0.113.80
mail2        A        203.0.113.81
server1      AAAA     2001:DB8:10::1
example.com. TXT      "we can write anyting in here"
```


- to get bind to ingest changes , restart the service 
- then use `dig @localhost < NS name>`


### Explanation of config 
- TTL == time to live 
- SOA == start of Authority
- IN == internet 
- serial: 
	- a zone config version number, incremented each time a zone config is updated. DNS cache will check serial number every so often and will refresh if out of sync
- refresh: 
	- tells other nameservers how long to wait before checking/refreshing their configs 
- retry: 
	- tells them how long to wait between failed refresh attempts 
- expire: 
	- tells them the utmost time to wait between failed refreshes before they stop trying 
- minimum: 
	- tells other servers how long to cache negative responses
- NS == nameserver 
- A == Authroitative record
- www== if someone uses www. at the beginning of their web entry
- MX == mail exchange
- AAAA == authoritave record for ipv6 addresses 


## Useful Commands 
```bash
# will only give the A record/s of the NS in question 
dig example.com +short

# get all assocciated records 
```