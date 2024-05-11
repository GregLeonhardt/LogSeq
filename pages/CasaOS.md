### TODO : Backup:
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
- ### Install:
	- ``wget -qO- https://get.casaos.io | sudo bash``
	- -OR-
	- ``curl -fsSL https://get.casaos.io | sudo bash``
- ### Uninstall:
	- ``casaos-uninstall``
- # Move root folder (for OMV)
	- CasaOS (by default) uses '/DATA' as it's root folder.  The problem is that this directory isn't part of an OMV volume.  Use the following steps to move it to a new location.
		- Stop and confirm that CasaOS services are stopped.
			- ``systemctl stop casaos*.service``
			- ``sudo systemctl status casaos.service``
		- Stop and confirm that Docker services are stopped.
			- ``sudo systemctl stop docker.*``
			- ``sudo systemctl status docker.service``
			- ``sudo systemctl status docker.socket``
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