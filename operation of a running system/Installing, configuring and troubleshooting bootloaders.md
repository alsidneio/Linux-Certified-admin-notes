
```zsh
# purpose of the bootloader is to start the linux kernal
# if bootlader wont start at all, use your  installation media and choose the 
# troubleshooting option

# shoose option 1 on the resuce menu and the boot will oad system on # /mnt/sysgroup

# go into the root 
chroot /mnt/sysroot

# once inside run 
	# for EFI
	grub2-mkconfig -o /boot/efi/EFI/centos/grub.cfg
	# for non EFI
	grub2-mkconfig -o /boot/grub2.grub.cfg

# Lookk for all block devices
lsblk

# look for sd or vd for physical or virtual disk, sda or vda 

# install grub on the /boot partision block
grub2-install /dev/sda

# if using efi use 
# dnf is centos package manger
dnf reinstall grub2-efi grub2-efi-modules shim

# exit twice to reboot the machine, then it will be tine to make changes to the config
# on next bootup
sudo vim /etc/default/grub

```