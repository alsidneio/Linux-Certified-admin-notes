
IMAPS allow us to read emails on different applixation 
common utility to setup imap on linux is dovecot
## Install and Enable Dovecot 
```bash 
# install dovecot
sudo dnf install dovecot

# start the service 
sudo systemctl start dovecot 

# enable autostart at boot time 
sudo systemctl enable dovecot

# add dovecot to the firewall 
sudo firewall-cmd --add-service=imap 
sudo firewall-cmd --add-service=imaps

# make firewall changes permanent  
sudo firewall-cmd --add-service=imap --runtime-to-permanent 
sudo firewall-cmd --add-service=imaps --runtime-to-permanent

```

## Configure Dovecot
- Config files for dovecot are locate at `/etc/dovecot/dovecot.conf`
- - More settings for dovecot are listed at `/etc/dovecot/conf.d/` directory
```vim 
# update/ write a protocols line to enable imap/imaps 
protocols = imap

#update the file to listen to connections 
listen = 10.11.12.9

# ======================= PORT CONFIGURATION =============================
# changing default ports that dovecot listens on is contained in 
	# /etc/dovecot/conf.d/10-master.conf under the inet_lister section
	# default should be 143 and 993 fir imap/imaps

service imap-login {
	
	inet_listener imap {
		#port = 143
	}
	
	inet_listener imaps {
		port = 993
		#ssl = yes
	}
}

# =================== MAILBOX CONFIGURATION ==============================
# the # /etc/dovecot/conf.d/10-mail.conf configures where the emails will
# be stored
# under the  mail_location = mbox setting 

mail_location = mbox:~/mail:INBOX=/var/mail/%u

# ================== TLS CONFIGURATION =================================
# TLS config is under /etc/dovecot/conf.d/10-ssl.conf

ssl = required # this makes it an imaps only server 
ssl = yes # this makes the server accept both imap/imaps
ssl = no  # this makes the server a imap only server 

ssl_cert = <> # locations 
ssl_key = <> # locations 

```


- 
## Definitions 
IMAP == Internet Message Access Protocol
IMAPS == IMAP Secur