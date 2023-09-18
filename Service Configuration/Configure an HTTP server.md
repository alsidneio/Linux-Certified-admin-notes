---
tags:
  - httpd
---
- the Http daemon listens for incoming 
	- unencrypted connections on `port 80` 
	- encrypted connection on `port 443`
- the Httpd configuration file is located at `/etc/httpd/conf/httpd.conf`
```bash 
# install httpd utility 
sudo dnf install httpd 

# start the service 
sudo systemctl start httpd

# enable autostart at boot 
sudo systemctl enable httpd 

#add the http and https as a service on the firewall 
sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --add-service=https --permanent 

# to enable https connection another package will need to be installled
sudo dnf install mod_ssl
```

## Httpd configuration 
```
# examples on how to configure can be see at 
man httpd.conf

# change defautl port 
Listen 8080

# only listen on a specific ip address:port
Listen 10.11.12.9:8080

# change email address where problems with server should be sent 
ServerAdmin admin@example.com

# ServerName, the name and port that your server is running 
# if you own a domain name, and that domain  is attatched to the server ip then you can use the domain 
ServerName: www.example.com:80
ServerName: 10.11.12.9:80

# set which files should be shown to the public 
DocumentRoot "/var/www/html"
```

### serving  multi-page site
- create a file in `/etc/httpd/conf.d/` directory 
```vim
#top block is always the default site
<VirtualHost *:80>
	ServerName store.example.com
	DocumentRoot /var/www/store/
</VirtualHost>

<VirtualHost *:80>
	ServerName blog.example.com
	DocumentRoot /var/www/blog/
</VirtualHost>
```

- to check if config is valid use `apachectl configtest`
- **Remember to add an index.html to the file locations defined by the virtual host**
- after the config changes do a reload 

## COnfiuring HTTPS
### Default SSL setting 
- install SSL module: 
	- `sudo dnf install mod_ssl -y`
- config located at /etc/httpd/conf.d/ssl.conf
- default listen port == 443
```vim 
#format of a config created from something like certbot
<VirtualHost *:443>
	ServerName example.com
	SSLEngine on 
	SSLCertificateFile 'path_to_cert'
	SSLCertificateKeyFile 'path_to_key'
</VirtualHost>
```

- httpd modules are located at /etc/httpd/conf.modules.d/
	- these modules can be enables or disabled as needed
	- optional modules are in `00-optional`