## INSTALL
	- Install the base OS from an ISO file.
		- The ISO file is on the Ventoy USB stick for both bare-metal and VirtualBox install.
		- When the install is complete, first time login:
			- Terminal:
				- User: root
				  Password: {Password given during install}
			- WEB interface:
				- User:  admin
				  Password: openmediavault
		- From the WEB interface complete the following:
			- NOTE: When you see a yellow banner across the top of the screen with the heading "Pending configuration changes". Left click on the checkmark then YES.
			  background-color:: yellow
			- User settings -> Change password:
			- User settings -> Dashboard:
				- Enable everything except:
					- System Time
					  Updates Available
					  Uptime
			- Under 'System Information' there will most likely be a checkmark under 'Updates available'.
				- Left click the checkmark.
				- When the list of updates are displayed, left click the "Install updates" icon.
					- Confirm and click 'YES'.
					- When the 'Close' button is displayed, click it.
			- Initialize all new disk drives.
				- Storage -> Disks
					- For each new disk drive:
						- Left click on the drive.
						- Left click on the 'Wipe' icon.
						- Left click 'Confirm'.
						- Left click 'Yes'.
						- Left click 'Quick'.
						- When displayed, left click 'Close'.
				- Enable and setup 'S.M.A.R.T.'
				- File System:
					- Create
					- Mount
				- Shared Folders:
					- home
					- docker
					- audio_visual
				-
	- Install OMV-EXTRAS
		- Complete instructions can be found at:
			- qq
		- From the command line run the following command:
			- ``wget -O - https://github.com/OpenMediaVault-Plugin-Developers/packages/raw/master/install | bash``
		-
- ### Stuff that needs a solution:
	- DONE Manage [[BtrFS]]
		- I will have to do this manually.
	- DONE Manage snapshot copy
		- Use the '[[snapper]]' package
	- DONE Scrub [[BtrFS]]
		- Use a 'cron' job to perform the scrub.
	- DONE Balance [[BtrFS]]
		- Though not absolutely required this is a good thing to do every once-in-a-while to prevent the over use of some drives while under using the remainder.  Like scrub above, this can be accomplished with the use of BtrFS commands and a cron job.
- ### Apps that I use:
	- | Application | Description | Available |
	  | LogSeq | Note taking | Yes |
	  | JellyFin | Media Server | Yes |
	  | Paperless-NGX | Document archive | Yes |
	  | Immich | Photo viewer & Organizer | Yes |
	  | SyncThing | Synchronize data between computers | Yes |
	  | WebTrees | Geanology | No |
	  | HumHub | Group messaging & chat | Yes |
	  | Mealie | Cooking & recipes | Yes |
	  | CrowdSec | Multi-System network security for Docker | Yes |
	  | Traefic | Reverse proxy for Docker | Yes |
	  | Transmission | Bittorrent client | Yes |
	  | Home Assistant | IOT Internet Of Things automation | Yes |
	  | PiHole | Intranet DNS | Yes |
	  | Uptime-Kuma | Network monitoring | Yes |
	  |
	-
	-