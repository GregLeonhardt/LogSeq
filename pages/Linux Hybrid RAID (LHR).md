# Project Requirements
	- Build a management environment that will configure and manage a RAID environment.
		- Requirements:
			- The base file system will be [[BtrFS]]
			- RAID Level is self determining (User does not get to choose).
				- A combination of RAID-1 and RAID-5 will be used.
			- Any number of any disk sizes may be grouped.
			- Snapshot will be available in some form.
- # Test 01:
	- Build a RAID-1 array using drives with the same size:
		- /dev/sda - 5GB
		  /dev/sda - 5GB
		- We will start by wiping the drives clean of all existing data and partitions.
			- ``parted -s /dev/sdb mklabel gpt mkpart primary btrfs 0% 100%``
			  ``parted -s /dev/sdc mklabel gpt mkpart primary btrfs 0% 100%``
		- Next we will create the RAID-5 storage pool using BTRFS.
			- ``mkfs.btrfs -d raid1 /dev/sdb1 /dev/sdc1``
				- NOTE: This does not work if there is an existing file system on any of the drives.  Use the '-f' command line option to force the remaking of the filesystem
		- Finally we will mount the new storage pool.
			- ``mkdir /mnt/raid1``
			  ``mount -t btrfs /dev/sdb1 /mnt/raid1``
				- NOTE: BTRFS sees all drives in the array as the same drive.  Thus any of the drives in the storage pool (/dev/sdb, /dev/sdc, /dev/sdc) could have been chosen when performing the mount.
	- # Test 02:
		- Fill the storage pool to 100%
			- rsync -av /usr/lib /mnt/raid1
	- # Test 03:
		- Build a RAID-5 array using mismatched drives:
			- /dev/sda - 2GB
			  /dev/sda - 3GB
			  /dev/sda - 4GB
			- We will start by wiping the drives clean of all existing data and partitions.
				- ``parted -s /dev/sdb mklabel gpt mkpart primary btrfs 0% 100%``
				  ``parted -s /dev/sdc mklabel gpt mkpart primary btrfs 0% 100%``
				  ``parted -s /dev/sdd mklabel gpt mkpart primary btrfs 0% 100%``
			- Next we will create the RAID-5 storage pool using BTRFS.
				- ``mkfs.btrfs -d raid5 /dev/sdb1 /dev/sdc1 /dev/sdd1``
			- Finally we will mount the new storage pool.
				- ``mount -t btrfs /dev/sdb1 /mnt/raid5``
					- NOTE: BTRFS sees all drives in the array as the same drive.  Thus any of the drives in the storage pool (/dev/sdb, /dev/sdc, /dev/sdc) could have been chosen when performing the mount.
		- # Test 02:
			- Fill the storage pool to 100%
				- rsync -av /usr/lib /mnt/raid1
- # Commands:
	- ## **gparted**
		- ``parted -s /dev/sdb mklabel gpt``
			- This command will create a partition table on the drive.
				- ** *NOTE: This command will remove any and all existing partitions and data from the drive.  USE IT WITH CAUTION!* **
				  background-color:: yellow
		- ``parted -s /dev/sdb mkpart primary btrfs 0% 50%``
			- This command will create a primary partition on the drive using the first half of the drive space.
		- NOTE: 'parted' commands may be stacked.  For example the above two commands could be executes as a single command:
			- ``parted -s /dev/sdb mklabel gpt mkpart primary btrfs 0% 50%``
- # Resources:
	- [VirtualBox image]([[VB-LHR]])
		- This is a VirtualBox development environment.