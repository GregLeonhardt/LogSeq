#	QuickConnect:
- ```
  QuickConnect ID:	GregLeonhardt
  DSM:			    http://quickconnect.to/GregLeonhardt
  Photo Station:	    http://quickconnect.to/GregLeonhardt/photo
  ```
- # SERVICES:
- ```
  Control Pannel => File Services => SMBIA/NFS		==> SMBIA - G06XDW4
  Control Pannel => File Services => SMBIA/NFS		==> NFS
  Control Pannel => File Services => rsync			==> rsync
  ```
- #	LDAP Server:
- #	SSH Keys:
- On the client (local) machine run:
- ```
  ssh-keygen -t rsa
  ssh-copy-id user@host-name
  ```
- #	Shared Folders:
- ```
  homes
  music
  photo
  STORA
  surveillance
  video
  VideoStation
  web
  ```
- #	File Services:
- ```
  SMB:			Enabled:	YES
  Workgroup		G0W6XDW4
  AFP:			Enabled:	YES
  NFS:			Enabled:	YES
  FTP:			Enabled:	NO
  TFTP:			Enabled:	NO
  rsync:			Enabled:	YES
  	port:		22
  ```
- #	USERS:
	- carol
		- Description:	Carol Riggio
		- Email:			Carolmk48@aol.com
		- User Groups:	drive
	- donald
		- Description:	Donald Riggio
		- Email:			Darigg99@aol.com
		- User Groups:	drive
	- greg
		- Description:	Greg Leonhardt
		- Email:			GregLeonhardt@gMail.com
		- User Groups:	administrators
	- tom
		- Description:	Tom Leonhardt
		- Email:			TGLeonhardt@gMail.com
		- User Groups:
- #	GROUPS:
	- drive
		- Description:
			- Synology Drive Users
		- Permissions:
			- homes			RO
			- music			RO
			- STORA			NA
			- video			RO
			- VideoStation	RO
			- web				NA
		- Quota:			10 GB
		- Applications:
			- Audio Station			A
			- DSM				A
			- Download Station		D
			- File Station		A
			- FTP				D
		- Notes Station		A
			- Synology Drive		A
			- Surveillance Station	D
			- Text Editor		A
			- Universal Search		A
			- Video Station		A
			- rsync				D
- #	Terminal & SNMP:
	- Telnet:	Enabled:	NO
	- SSH:		Enabled:	YES
- #	BACKUP TO SYNOLOGY MOUNTED USB:
- ```
  rsync -av --delete --exclude "@*" /volume1/homes               /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/music               /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/photo               /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/STORA/MyComputers   /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/STORA/MyLibrary     /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/STORA/NoBackup      /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/STORA/OneOff        /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/STORA/Tape-Cheyenne /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/STORA/Torrents      /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/STORA/VirtualBox    /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/video               /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/VideoStation        /volumeUSB1/usbshare/. ;\
  rsync -av --delete --exclude "@*" /volume1/web                 /volumeUSB1/usbshare/.
  ```
- #	BACKUP TO LOCAL USB:
- ```
  rsync -av --delete --exclude "@*" greg@synology:/volume1/homes               /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/music               /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/photo               /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/STORA/MyComputers   /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/STORA/MyLibrary     /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/STORA/NoBackup      /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/STORA/OneOff        /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/STORA/Tape-Cheyenne /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/STORA/Torrents      /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/STORA/VirtualBox    /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/video               /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/VideoStation        /media/greg/CrashPlan/. ;\
  rsync -av --delete --exclude "@*" greg@synology:/volume1/web                 /media/greg/CrashPlan/.
  ```
-