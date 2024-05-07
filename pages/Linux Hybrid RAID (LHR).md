# Project Requirements
	- Build a management environment that will configure and manage a RAID environment.
		- Requirements:
			- The base file system will be [[BtrFS]]
			- RAID Level is self determining (User does not get to choose).
				- A combination of RAID-1 and RAID-5 will be used.
			- Any number of any disk sizes may be grouped.
			- Snapshot will be available in some form.
- # Experiment #01
	- Build a RAID-5 array using mismatched drives:
		- /dev/sda - 2GB
		  /dev/sda - 3GB
		  /dev/sda - 4GB
		- W
		- ``gprted -s /dev/sdb mklabel gpt``
		  ``gprted -s /dev/sdc mklabel gpt``
		  ``gprted -s /dev/sdd mklabel gpt``
- # Commands:
	- ## **gparted**
		- ``gprted -s /dev/sdb mklabel gpt``
			- This command will create a partition table on the drive.
				- ** *NOTE: This command will remove any and all existing partitions and data from the drive.  USE IT WITH CAUTION!* **
				  background-color:: yellow
		- ``parted -s /dev/sdb mkpart primary btrfs 0% 50%``
			- This command will create a primary partition on the drive using the first half of the drive space.
		- NOTE: 'parted' commands may be stacked.  For example the above two commands could be executes as a single command:
			- ``gprted -s /dev/sdb mklabel gpt mkpart primary btrfs 0% 50%``
- # Resources:
	- [VirtualBox image]([[VB-LHR]])
		- This is a VirtualBox development environment.