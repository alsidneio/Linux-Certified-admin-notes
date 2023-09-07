```zsh
systemctl reboot
sudo systemctl reboot --force 
sudo systemctl poweroff --force
sudo systemctl reboot --force --force # caustion this is a last resort

# instructing linux to shutodoen on its own 
# shutdown at 2 am 
sudo shutdown 02:00

# shutdown in 15 mins
sudo shutdown +15

# to reboot use the -r option 
sudo shutdown -r 02:00

# to send a wall message to users before shutdown 
sudo shutdown -r +1 'restart is scheduled save ya shit'
```