- Follow the instructions for [[VirtualBox OS Install]] with the following changes.
	- My first instinct was to do the development on a server (no graphical user interface).  This didn't work very well.  The primary problem is that I can't increase the display size.  I suppose I could 'ssh' into the server with something like putty but it seams easier to just install a desktop environment.  So I am switching to Linux Mint Debian Edition.
		- The following are for "**lmde-6-cinnamon-64bit.iso**"
			- I configured the test system with:
				- 16 GB disk space
				- 8 GB memory
				- 4 CPUs
		- RAID Drives:
			- Controller:
				- LsiLogic (Default SCSI)
					- ``lhr_1  -  5 GB``
					- ``lhr_2  -  5 GB``
		- Installed packages used for development:
			- ```
			  sudo apt install -y \
			  	flatpack \
			  	gparted \
			      mdadm \
			      pip \
			      vim
			  flatpak install -y \
			  	DBeaver    (app/io.dbeaver.DBeaverCommunity/x86_64/stable)
			  ```
		- Installed packages needed by the SimpleRAID package.
			- ```
			  pip install
			  	------
			  ```
		-
-