- Probably because it is what I am using for just about everything else I will start with a Debian image.
	- The following are for "**debian-12.5.0-amd64-netinstall.iso**"
		- I configured the test system with:
			- 16 GB disk space
			- 8 GB memory
			- 4 CPUs
		- Just do a normal Debian install until you get to the software selection menu.
			- Uncheck 'Debian desktop environment' and 'GNOME' leaving 'standard system utilities' as the ONLY checked box.
		- After first boot do the following:
			- I was hoping that this would allow me to stretch the window to make a larger terminal screen.  So far no luck.
			  background-color:: yellow
			- ```
			  login as root
			  VB-Devices -> Insert Guest Additions CD image
			  mount /dev/cdrom /mnt
			  cd /mnt
			  ./VBoxLinuxAdditions.run
			  reboot
			  ```
		- When the reboot completes:
			-