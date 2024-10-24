# Create a new VirtualBox image with the following:
title:: VirtualBox OS Install
- ```
  debian-12.0.0-amd64-netinst.iso
  memory   4096 MB
  processor   4
  ```
	- Shared Folder:
		- `C:\Users\greg\Documents\Linux   /home/greg/Documents/Linux`
	- Install the following components:
		- ```
		  Debian desktop environment
		  Gnome desktop
		  MATE desktop
		  SSH server
		  standard system utilities
		  ```
		- NOTE:    Unless noted above, use the default settings.
- # After the install is complete:
	- ## Add {UserName} to sudoers:
		- Edit /etc/sudoers and insert the following lines of text:
			- `{UserName} ALL ALL ALL`
				- `su - root`
				- `vi /etc/sudoers`
	- ## Add a ‘bin’ directory and update the ‘PATH’ variable
		- Edit .bashrc and insert the following:
			- `export PATH=.:~/bin:$PATH`
				- `mkdir ~/bin`
				- `vi ~/.bashrc`
	- ## Install VirtualBox Guest Additions
		- `su - root`
		- `mkdir /mnt/cdrom`
		- `mount /dev/cdrom /mnt/cdrom`
		- `cd /mnt/cdrom`
		- `./VBoxLinuxAdditions.run`
		- `reboot`
	- ## Devices -> Insert Guest Additions CD image
	- ## Add VirtualBox File System Group:
		- ``sudo usermod -a -G vboxsf `whoami` ``
	- ## Add VirtualBox Shared Folders:
	- Shared folders are created within the VirtualBox application.  Once created they may be mounted auto mounted when the guest OS is booted or allow the guest OS to mount them.  When auto mounted they will belong to 'root' with a group of 'vboxsf'.  In this case users MUST be granted permission to group 'vboxsf' to be able to access the mounted files.
	- Some applications look at or even change the the owner and/or group.  In many of these cases the application simply will not work.  If the application is only looking at the owner or group the shared folder may be mounted within the guest OS using the 'fstab' file as below.
	- NOTE: When creating shared folders for the guest OS to mount, DO NOT check the Auto Mount check box and the mount path may be left empty.
- ## Mounting a VirtualBox Shared Folder
	- Edit /etc/fstab with the following:
		- `Linux /home/greg/Documents/Linux vboxsf rw,nodev,relatime,umask=007,iocharset=utf8,uid=1000,gid=1000 0 0`
		- I had a problem with the above and modified the mount to the following:
			- `Linux /home/greg/Documents/Linux vboxsf rw,nodev,relatime,umask=007,uid=1000,gid=1000 0 0`
-