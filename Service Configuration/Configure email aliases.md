state: 
	- server is configured to receive emails
	- we received an email to aaron@example.com
		- if a user is already configured its stored at `/var/spool/mail/aaron`
	- we want to let our users send emails to more accounts without having to create more user accounts
		- contact@example.com
		- advertising@example.com
		- complaints@example.com 
	- the user aaron is the manager for the previous account so we can just forward those email to aaron@example.com 

## Using postfix to create an email server 
```bash 
# install postfix
sudo dnf install postfix 

# start the service 
sudo systemctl start postfix

# enable auto start at boot 
sudo systemctl enable postfix

#postfix is configured to work with @localhost domain
# send test email with sendmail utility 
# this should create a file /var/spool/aaron with the corresponding info 
sendmail aaron@localhost <<< "Hello, THis is a test email."


```

### Creating an email alias
- alias definition file is stored at `/etc/aliases`
	- define the email alias like: `advertising: aaron`
	- an alias defined as: `contact: aaron,john,jane` will forward the email to 3 different accounts
- tell postfix about the new alias
	- `sudo newaliases`
- then use the `sendmail` utility to test 
