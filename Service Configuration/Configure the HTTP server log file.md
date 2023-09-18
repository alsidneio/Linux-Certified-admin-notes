---
tags:
  - httpd
  - logs
  - configuration
---
Config located in `/etc/httpd/conf/httpd.conf`
- There are two log files
	  1. error log: 
	  2. access logs: 
		  1. who visited 
		  2. pages access 
		  3. browser used 
- config path can be made under the `ErrorLog` param 
- Default log level is set to `warn`
- keep a seperate log for each veirtual host in the httpd config file
```vim 
<VirtualHost *:80>
	ServerName store.example.com
	DocumentRoot /var/www/store/
	CustomLog /var/log/httpd/store.example.com.log combined 
	ErrorLog /var/log/httpd/store.example.com_error.log combined 
</VirtualHost>

<VirtualHost *:80>
	ServerName blog.example.com
	DocumentRoot /var/www/blog/
</VirtualHost>
```