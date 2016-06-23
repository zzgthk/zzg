Installation of Ubuntu on Dell Tower5810 

## Preparation

1. write a ubuntu iso to a U disk.

2.  download the display driver of Dell Tower5810 of Linux version: NVIDIA-Linux-x86_64-361.45.11.run, and copy it to the U disk.

2. use another display which can support dvi port, and connect the display card and this display with the dvi cable.

## Installation

1. plug in the U disk to the Dell Tower5810 and start it.

2. when the computer start, press F12 to enter bios setup, and select the U disk to boot

3. then install ubuntu according to the guide of Ubuntu and then reboot the computer

4. copy the display driver to the Ubuntu, then connect to the network, then run the following command：
	
	sudo apt-get update
	sudo apt-get install build-essential linux-headers-`uname -r`  dkms
	
	After above, press ctrl + alt + F1, to enter text mode session. then do the following command:
	
  sudo  /etc/init.d/lightdm stop
	sudo  ./NVxxx.run # first time it will failed, then reboot, press ctrl + alt + F1 and do stop and run install driver again.
	
## FAQ

1.if no grub selections, then use:

  sudo update-grub

Reboot, it will ok.
