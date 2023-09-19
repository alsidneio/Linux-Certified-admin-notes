```bash 
#install 
sudo apt install virt-manager

#download a disk image 
wget <some image address>

# inspect the image 
qemu-img info <image-name>

# expand the size of a virtual disk 
qemu-img resize <imagName>.img 10G

# move your image file to /var/lib/libvirt/images/

# start the vrtual machine from image 
virt-install \
--osinfo ubuntu22.04 \ # set OS type
--name ubuntu1 \ # 
--memory 1024 \ # set memory of the machine
--vcpus 1 \
--import \
--disk /var/lib/libvirt/images/ubuntu-22.04.img \ 
--graphics none

```