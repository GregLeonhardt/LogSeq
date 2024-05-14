## Definitions:
	- For simplicity the following will use `/srv/dev-disk-by-uuid-71a84d92-2675-45de-b343-cd7565537305/" to identify the 'File system'.  This directory will be different on your system.
- ## Sub-Volumes:
	- ### Compose Files:
		- Name:
		- File system:
	- ### Data:
	- ### Backup:
	- ### Docker
- ## Install:
- Docker uses three directory roots for all the Docker images, configurations, and data.  Create them as follows:
	- Create a new shared filesystem for Docker stuff:
		- Storage -> Shared Folders -> Create
			- Name: Docker
			  File system: {File System Location}
	- Configure 'snapper' to take regular snapshot copies:
		- ``ln -s {/path/to/subvolume} /volume1/Docker``
		- ``snapper -c Docker create-config /volume1/Docker``
		- Edit ``/etc/snapper/configs/Docker`` as needed.
	- Create directories for the various docker parts:
		- ``mkdir /volume1/Docker/Compose``
		- ``mkdir /volume1/Docker/Data``
		- ``mkdir /volume1/Docker/Storage``
- We are ready to start downloading and installing the OMV Extras package.
	- ``wget -O - https://github.com/OpenMediaVault-Plugin-Developers/packages/raw/master/install | bash``
- Refresh the Open Media Vault WEB interface (F5) and go to:
	- System -> omv-extras
		- Check the 'Docker repo' checkbox.
		- Click the Save button
- NOTE: Another WEB interface refresh may have been required here.  Not sure.
  background-color:: red
- Install 'Docker-Compose'
	- Install System -> Plugins -> openmediavault-compose
- Configure openmediavault-compose:
	- Services -> Compose -> Settings
		- Compose Files -> Shared folder
			- Select the Docker subvolume.
		- Data -> Shared Folder
			- Select any other subvolume
				- NOTE: Selecting the same subvolume as above will result in an error.
				  background-color:: red
		- Docker -> Docker storage
			- /volume1/Docker
	- Click the 'Save' button.
- NOTE: This is where things get *VERY* murky.  I can't find anything that gives any kind of a list of available Docker containers.  I guess this is why at this point all the tutorials install some sort of Docker manager.  'Portainer' is the most common but probably the oldest.
  background-color:: yellow
- To install and run portainer, run the following command:
	- ``docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest``
		- Before we can connect to this (or any other) Docker container we must punch a hole in the OMV firewall.