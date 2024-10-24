- ***CasaOS Is a bust.***
  background-color:: red
  id:: 663fe8b4-e0f4-42d0-890c-831f21afa06d
	- There may be a way to do it but I was unsuccessful at moving the '/var/lib/casaos' and 'DATA' directories to BtrFS. I followed the directions but it just wouldn't work.  I tried to move the data and link the directories and I also followed the directions for changing the location of '/var/lib/casaos'.  In the end when the system restarted it would just create a new '/var/lib/casaos' directory and it couldn't see anything in the /DATA directory.  Maybe some day, or some year I'll come back and try again but I am done for now.
	  background-color:: red
- ### Install:
	- ``wget -qO- https://get.casaos.io | sudo bash``
	- -OR-
	- ``curl -fsSL https://get.casaos.io | sudo bash``
	- When running under Open Media Vault (OMV) the CasaOS root folder and the 'DATA' folders need to be moved to the BtrFS.
		- Create a shared BtrFS folder:
			- From OMV desktop: Storage -> Shared Folders -> Create
				- Name: CasaOS
				  File system: {select}
		- Snapper snapshot copies:
			- ``ln -s {PATH_TO}/CasaOS /volume1/CasaOS``
			- ``snapper -c CasaOS create-config /volume1/CasaOS``
			- Edit '/etc/snapper/configs/CasaOS' to set the snapshot configuration.
		- Stop all CasaOS daemons.
			- ``systemctl stop casaos*.service``
			- ``systemctl stop docker.*``
		- Create CasaOS root and data directories.
			- ``mkdir /volume1/CasaOS/var_lib_casaos``
			- ``mkdir /volume1/CasaOS/DATA``
		- Edit the CasaOS configuration file at '/lib/systemd/system/docker.service'
			- From:
				- ``ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock``
			- To:
				- ``ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock --data-root /volume1/CasaOS/var_lib_casaos``
		- Move all existing data from the boot drive to the RAID volume
			- ``mv /var/lib/casaos/* /volume1/CasaOS/var_lib_casaos/.``
			- ``mv /DATA/* /volume1/CasaOS/DATA/.``
		- Delete the old folders.
			- ``rm -rf /var/lib/casaos``
			- ``rm -rf /DATA``
		- Create symbolic links from the new directories back to where CasaOS expects them to be.
			- ``ln -s /volume1/CasaOS/var_lib_casaos /var/lib/casaos``
			- ``ln -s /volume1/CasaOS/DATA /DATA``
		- Reboot to activate the new configuration.
			- ``reboot``
- ### TODO : Backup:
  :LOGBOOK:
  CLOCK: [2024-05-11 Sat 07:36:56]--[2024-05-11 Sat 07:37:00] =>  00:00:04
  :END:
	- Backup both '/var/lib/casaos' and '/DATA'.
- ### TODO Move data from boot disk to RAID disk.
  :LOGBOOK:
  CLOCK: [2024-05-11 Sat 07:35:56]--[2024-05-11 Sat 07:36:04] =>  00:00:08
  :END:
	- Move both '/var/lib/casaos' and '/DATA'.
- ### Pre-Install:
	- When running under Open Media Vault (OMV):
		- The web interface for OMV must be changed as by default both OMV and CasaOS use port 80.
			- System -> Workbench: Port
				- Change from '80' to just about anything else.  '8080' is a good choice.
		- Create a subvolume for CasaOSs Docker containers.
			- Storage -> Shared Folders + (create)
				- Name: docker
				- File system: (use the pull down to select)
			- Create an automated snapshot copy using snapper.
				- ``snapper -c docker create-config /volume1/docker``
				- Edit '/etc/snapper/configs/docker' as needed
- ### Uninstall:
	- ``casaos-uninstall``
- # Move root folder (for OMV)
	- CasaOS (by default) uses '/DATA' as it's root folder.  The problem is that this directory isn't part of an OMV volume.  Use the following steps to move it to a new location.
		- Stop and confirm that CasaOS services are stopped.
			- ``systemctl stop casaos*.service``
			- ``systemctl status casaos.service``
		- Stop and confirm that Docker services are stopped.
			- ``systemctl stop docker.*``
			- ``systemctl status docker.service``
			- ``systemctl status docker.socket``
		- Create the new directory for images and volumes.
			- ``mkdir -p /path/to/new/location``
		- Edit the CasaOS configuration file at '/lib/systemd/system/docker.service'
			- From:
				- ``ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock``
			- To:
				- ``ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock --data-root /path/to/new/location``
			- Copy the existing content from `/var/lib/docker` to the new path.
				- ``rsync -avxP /var/lib/docker/ /path/to/new/location``
			- Copy the existing content from `/DATA` to the new path.
				- ``rsync -avxP /DATA/ /path/to/new/location``
			- Restart the machine.
				- ``reboot``
			- If everything goes well in couple of days, feel free to delete '/var/lib/docker/*' to reclaim some storage space.
				- ``rm -rf /var/lib/docker/*``
			- Then delete the old root folder.
				- ``rm -rf /DATA``