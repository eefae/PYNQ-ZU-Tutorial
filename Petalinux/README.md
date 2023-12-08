# Introduction
Today, we want to use Petalinux on PYNQ-ZU. For this goal, we need to follow the flow below. First, We will create a Vivado project for Petalinux. Second, use docker to build the environment. Last, generate a Petalinux project. After the last step, we will get 4 files we need. The first three files are for booting the Linux kernel, and the last one can generate a Linux file system.
1. BOOT.bin
3. boot.scr
4. image.ub
5. rootfs.tar.gz
# Vivado Project
<img width="562" alt="image" src="https://github.com/jyun-teng-huang/Petalinux_Docker/assets/104624317/42420634-d7f0-45ef-9fdb-1016e598b8f8">

# Docker environment
## Download the Ubuntu 18.04.2 LTS image:
```
sudo docker pull ubuntu:bionic-20190515
```
## Create and run a container:
```
sudo docker run --name=petalinux_pynqzu_bionic-20190515 -e HOME=/workspace -w /workspace -v /home/jt/Petalinux:/workspace -it ubuntu:bionic-20190515 /bin/bash
```
## Set a password as the root user
```
passwd
```
## Setup locale
```
echo "LC_ALL=en_US.UTF-8" >> /etc/environment
echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen
echo "LANG=en_US.UTF-8" >> /etc/locale.conf
locale-gen en_US.UTF-8
```
## Install Petalinux dependency package:
```
dpkg --add-architecture i386
apt update
apt install bc gawk vim sudo gcc gcc-multilib net-tools xterm autoconf libtool python3 less rsync texinfo zlib1g-dev build-essential -y
apt install zlib1g-dev:i386 libncurses5-dev -y
```
## Set default shell to bash
```
ln -sf /bin/bash /bin/sh
```
## Create a new User and add it to the sudoers file
```
adduser USERNAME
chmod 744 /etc/sudoers
echo "USERNAME ALL=(ALL:ALL) ALL">>/etc/sudoers
```
## Launch the container
```
sudo docker start petalinux_pynqzu_bionic
sudo docker exec -it petalinux_pynqzu_bionic-20181018 /bin/bash
```
# Create the Petalinux project:
Do not use the root user to run the command below.
```
source /workspace/install/settings.sh
petalinux-create -t project --template=zynqMP -n petalinux_project
cd petalinux_project
petalinux-config --silentconfig --get-hw-description XXX.xsa
petalinux-build
cd ./images/linux
petalinux-package --boot --fsbl zynqmp_fsbl.elf --u-boot u-boot.elf --pmufw pmufw.elf --fpga system.bit --force
```
