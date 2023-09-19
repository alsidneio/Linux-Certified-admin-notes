- for this demo MariaDB as the server 
```
# install mariadb
sudo dnf install mariadb-server

# start the service 
sudo systemctl start mariadb.service

#enable it to start at boot time 
sudo systemctl enable mariadb.service

# allow the service connections through the firewall
sudo firewall-cmd --add-service=mysql

# make the firewall change permanent
sudo firewall-cmd --add-service=mysql --permanent

```

## secure the database 
- after initial installation run `mysql_secure_installation`
	- after answering yes to all the questions, to log in as root you must provide a password: `mysql -u root -p`

## Mariadb COnfig files 
- located at: 
	- /etc/my.cnf
	- /etc/my.cnf.d/mariadb-server.cnf
```vim
...
[mysqld]

# this is the location of the DBs
datadir=/var/lib/mysql 
 
#config where other applications can connect to the service
socket=

#directory where errors are going to be logged 
log-error=

#pid underwhcih the DB daemon is running
pid-file=
...

[galera]
bind-address=0.0.0.0
```