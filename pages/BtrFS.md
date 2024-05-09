### Drive initialization:
	- Use the built-in 'parted' command to perform the initialization.  It will create the drive label and create a primary partition.
		- ``parted -s {DRIVE-ID}`` mklabel
	- ``parted -s /dev/sdb mklabel gpt mkpart primary btrfs 0% 100%``