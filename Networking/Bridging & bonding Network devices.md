## Bridging 
- to bridge is creating a connection between networking interfaces/devices
	- for the purpose of connecting two different networks
- bridges are called controllers & devices on the bridge are called ports

## Bonding 
- to bond is taking multiple network devices act as one interface for the network
- this is where load balancing comes in 
- Benefits of bonding: 
	- makes system resilient in case of interface failure 
	- increase network thoughput 
	- makes connections more reliable (slowdowns)
	- 
- Bond modes (default == 0)
	- 0 == round-robin
		- there is an arder in which interfaces will be used 
	- 1 == active-backup
		- one interface at a time until backup is needed
	- 2 == XOR
		- strict source and destination route
	- 3 == broadcast
		- send everythoing to everyone 
	- 4 == IEEE 802.3ad
		- increasedd transfer rates 
	- 5 == adaptive transmit load balancing
		- will send data through interface that is least busy
	- 6 == adaptive load balancing
		- load balance both outgoing/ incomeing traffic
