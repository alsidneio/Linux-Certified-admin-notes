-  some services boot up in a particular order 
- if a service is enabled it will try to start automatically
- if important apps crash there will be an automatic restart
- ALL OF THIS IS HANDLED BY THE INIT SYSTEM
- units of the init system
	- service 
	- socket
	- device 
	- timer

see commands by running `man systemd.service`

```bash
# lookiung at the service for the ssh, will give you the service config
systmectl cat sshd.service

# if you want to edit a service file
sudo systemctl edit --full sshd.service

# return service file to its default setting
sudo systemctl revert sshd.service

# to the status of a aservice 
sudo systemctl status sshd.service

# to stop a service sudo systemctl stop sshd.service
sudo systemctl stop sshd.service

# to manuallt start a service sudo systemctl 
sudo systemctl start sshd.service

# to restart a service sudo systemctl 
sudo systemctl restart sshd.service 
sudo systemctl reload sshd.service # this is a more graceful shutdown 

# an automatice gracefail restar
sudo systemctl reload-or-restart sshd.service

# to stop ssh to this device
sudo systemctl disable sshd.service

# check if a service is enabled
sudo systemctl is-enabled sshd.service

# to enable and start  a service
sudo systemctl enable --now sshd.service

# to disable and stop  a service
sudo systemctl disable --now sshd.service

# services that cannot be enables or disabled are called 'masked' service
sudo systemctl mask atd.service

# to unmask a service 
sudo systemctl unmask atd.service

#list all service units available on machine 
sudo systemctl list-units --type service --all



```