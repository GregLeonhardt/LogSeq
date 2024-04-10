howtoinstall:: Part of the distributed system.

- # DESCRIPTION
	- lsblk lists information about all available or specified block devices.  The lsblk command reads the sysfs file system and udev db to gather information.  If the udev bd is not available or lsblk is compiled without udev support, then it tries to read LABELs, UUIDs and filesystem types from the block device. In this case root permissions are necessary.
	  
	  By default, the command prints all block devices (except RAM disks) in a tree-like format. The same device can be repeated in the tree if it relates to other devices. The --merge option is recommended for more complicated setups to gather groups of devices and describe complex N:M relationships.
- ## USEFULL OPTIONS
	- `-f, --fs`
		- Output info about filesystems. This option is equivalent to -o NAME,FSTYPE,FSVER,LABEL,UUID,FSAVAIL,FSUSE%,MOUNTPOINTS. The authoritative information about filesystems and raids is provided by the blkid(8) command.
- ### EXAMPLES:
	- `lsblk -f`
		- ```
		  NAME FSTYPE FSVER LABEL UUID FSAVAIL FSUSE% MOUNTPOINTS
		  sda
		  ├─sda1 ext4 1.0 0ddabb03-3a97-41d2-ae54-25ff3d289673 1.4G 92% /
		  ├─sda2
		  └─sda5 swap 1 d86578bc-f788-4e7b-9b99-8da7ae422109 [SWAP]
		  sdb
		  └─sdb1 swap 1 84ea49f0-c96e-4467-b0ee-ea1d5da05cdd [SWAP]
		  sr0
		  ```