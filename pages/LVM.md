HowToInstall:: `sudo apt install -y lvm2`

- ## List all available HDD:
	- `lvmdiskscan`
- ## Create a new volume group:
	- `mkfs -t ext4 /dev/sdb`
	- `fdisk /dev/sdb`
		- ```
		  n  --  New partition
		  p  --  Primary partition
		  1  --  First partition
		  ?? --  Accept the default first sector
		  ?? --  Accept the default last sector
		  w  --  Write changes and exit
		  ```
	- `pvcreate /dev/sdb1`
	- `vgcreate vga /dev/sdb1`
	- `lvcreate -n hyperbackup -l +100%FREE vga`
	- `mkfs -t ext4 /dev/vga/hyperbackup`
	- `mkdir /mnt/hyperbackup# chmod 700 /vga/hyperbackup`
	- `blkid /dev/vga/hyperbackup`
- # Add to /ext/fstab
	- ```
	  UUID={uuid} /vga/hyperbackup ext4 defaults 0 0
	  ```
	- `reboot`
- # To add additional HDDs to the volume
  
  -`mkfs -t ext4 /dev/sd?`
  
  -`fdisk /dev/sd?`
	- ```
	  n  --  New partition
	  p  --  Primary partition
	  1  --  First partition
	  ?? --  Accept the default first sector
	  ?? --  Accept the default last sector
	  w  --  Write changes and exit
	  ```
- `pvcreate /dev/sd?1`
- `vgscan`
- `vgextend vga /dev/sd?1`
- `df -h`
- `lvextend -l +100%FREE /dev/mapper/vga-hyperbackup`
- `resize2fs /dev/mapper/vga-hyperbackup`
- #  Prepare for ssh:
- `su - hyperbackup`
- `mkdir .ssh`
- `touch .ssh/authorized_keys`
- Login to synology:
- Edit /etc/hosts to add the hyperbackup server.
- `cat ~/.ssh/id_rsa.pub | ssh hyperbackup@hyper-backup 'cat >> ~/.ssh/authorized_keys`