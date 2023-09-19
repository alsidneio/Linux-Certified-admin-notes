- virsh is a program to help managae VMs via terminal 
## Setup 
```bash 
# install
sudo dnf install libvirt qemu-kvm 

# 
```

## configuration 
```vim 
<domain type='qemu'>
	<name>TestMachine</name>
	<memory unit="GiB">1</memory>
	<vcpu>1</vcpu>
	<os>
		<type arch='x86_64'>hvm</type>
</domain>
```

## VM management 
```bash 
# start the vm from the configfile 
virsh define testmachine.xml

# list active domains in virsh
virsh list 

# list all domains 
virsh list --all

#start a patricular domain 
virsh start <domainName>

# rebbot a VM 
virsh reboot <domainName>

# FOrce reset a mavhine 
virsh reset <domainName>

# shutdown a michine
virsh shutdown <domainName>

# force a hard power off 
virsh destroy <domainName>

# delete a VM 
virsh undefine <domainName>

# remove VM and data 
virsh undefine --remove-all-storage <domainName>

# start up a VM when the host starts 
virsh sutostart <DomainName>

# disable autostart 
virsh autostart --disable <domainName>

# get VM HW info 
virsh dominfo <domainName>

# update/change VM HW settings 
virsh set 

# change number of cpus 
virsh setvcpus <domainName> 2 --config

# change max numbers of CPUS
# must restart VM for these changes to apply
virsh setvcpus <domainName> 2 --config --maximum 

# set memeory size to 80M
sudo virsh setmaxmem VM2 80M --config
```