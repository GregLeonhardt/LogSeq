### Drive initialization:
	- Use the built-in 'parted' command to perform the initialization.  It will create the drive label and create a primary partition.  Do this for every drive that will be added to the array.
		- ``parted -s {DRIVE-ID} mklabel gpt mkpart primary btrfs 0% 100%``
		- EXAMPLE:
			- ``parted -s /dev/sdb mklabel gpt mkpart primary btrfs 0% 100%``
- ### Make an array:
	- #### RAID-1
		- `````mkfs.btrfs -d raid1 {DRIVE_1}1 {DRIVE_2}1`````
	- #### RAID-5
		- ``mkfs.btrfs -d raid5 {DRIVE_1}1 {DRIVE_2}1 {DRIVE_}1``