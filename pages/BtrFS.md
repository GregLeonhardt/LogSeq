### Drive initialization:
	- Use the built-in 'parted' command to perform the initialization.  It will create the drive label and create a primary partition.  Do this for every drive that will be added to the array.
		- ``parted -s {DRIVE-ID} mklabel gpt mkpart primary btrfs 0% 100%``
		- EXAMPLE:
			- ``parted -s /dev/sdb mklabel gpt mkpart primary btrfs 0% 100%``
- ### Make an array:
	- #### RAID-1
		- ``mkfs.btrfs -d raid1 {DRIVE_1}1 {DRIVE_2}1``
		- EXAMPLE:
			- ``mkfs.btrfs -d raid1 /dev/sdb1 /dev/sdc1``
	- #### RAID-5
		- ``mkfs.btrfs -d raid5 {DRIVE_1}1 {DRIVE_2}1 {DRIVE_3}1``
		- EXAMPLE:
			- ``mkfs.btrfs -d raid5 /dev/sdb1 /dev/sdc1 /dev/sdd1``
	- NOTE: You do NOT mount the file system.  it will be imported from [[OpenMediaVault OMV]]
	  background-color:: gray