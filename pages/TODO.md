# To Do
	- ## [[Paperless-ngx]]
		- ### Paperless-ngx is a free and open-source document management system that transforms physical documents into a searchable online archive.
			- ~~~Install Docker container.~~~
			- ~~~Configure~~~
		- ### Follow-up: The container is installed and running as a Dockage container but I want to move the data to the Docker dataset.
			- This shouldn't be anything more than copy the data over and modify the config.yaml file to the new locations.
	- ## DeDup
	  collapsed:: true
		- ### RecipeArchive
	- ## Backup to local HDD
		- ### ~~Phase 1 Local HDD backup.~~
		  collapsed:: true
			- I should be able to create a local spanned disk pool using the USB drives I have laying around.
				- ``zpool create  BACKUP /dev/sdx /dev/sdy /dev/sdz``
					- Where BACKUP is the pool name
					- Where /dev/sd? are the HDDs
			- To expand the zpool run the following:
				- ``zpool add  BACKUP /dev/sdw``
					- Where BACKUP is the pool name
					- Where /dev/sdw is the HDDs
		- ### Phase 2 CrashPlan
		  collapsed:: true
			- I think that I will be able to run Crashplan in a virtual OS on the TrueNAS server.
			- In the perfect world all I will need to do is to spin up an UBUNTU system and give it access to the DataSets I want backed up.
			- I just saw that TrueNAS 25.04 is changing the way virtual environments work so I think that I will wait until I install it before attempting this.
	- ## [[Mealie]]
	  collapsed:: true
		- ### Mealie is **a self hosted recipe manager and meal planner** with a RestAPI backend and a reactive frontend application built in Vue for a pleasant user experience for the whole family.
		  collapsed:: true
			- Install Docker container
			- Import existing data to the new container.
	- ## Shinobi or ZoneMinder
	  collapsed:: true
		- ### Free and open-source option, modern video surveillance solution known for its ease of use.
			- Install Docker container
			- Configure
				- Cameras
				- Timelaps
				- Purge files
	- ## [[WebTrees]]
	  collapsed:: true
		- ### WebTrees is a free, open-source, web-based genealogy application that allows users to create, manage, and share family trees online.
			- ~~Install Docker container~~
			- Configure for external internet access (NGINX)
			- Add data
	- ## [[Git]]
	  collapsed:: true
		- ### Git is a distributed version control system used to track changes in computer files, especially source code during software development.
			- Install Docker container
			- Move existing repos to the new container.
- # Done
	- ## [[Immich]]
	  collapsed:: true
		- ### Immich is a free, open-source, self-hosted photo and video management solution
			- ~~Install Docker container~~
			- ~~Configure~~
			  collapsed:: true
				- Nick
				- Greg
				- Louise
				- Tom
				- Jason
				- Jane
				- Norma
	- ## [[DDNS Updater]]
	  collapsed:: true
		- ### DDNS Updater checks for changes to the external IP address of a Microsoft Windows computer, and updates a dynamic DNS (DDNS) service whenever a change is detected.
			- ~~Install the Docker container~~
			- ~~Configure~~
				- Client Key: f5862204bfb111efa921e901e67ca7b5
				- UserName: gregleonhardt
				- 508r.dyndns.org
				- humhub.dyndns.org
				- immich.myphotos.cc
				- webtree.dyndns.org
				- myrecipies.homeip.net
				- familytree.homeip.net
				- humhub.homeip.net
		- ### ~~Follow-up: The container is installed and running as a TrueNAS container but I am moving everything over to Dockge so I am going to have to do it all over again.~~
	- ## [[Jellyfin]]
	  collapsed:: true
		- ### Jellyfin is a free and open-source media server that allows users to organize, manage, and stream their media files from a dedicated server to various devices.
			- ~~Install Docker container~~
			- ~~Configure~~
		- ### ~~Follow-up: The container is installed and running as a TrueNAS container but I am moving everything over to Dockge so I am going to have to do it all over again.~~
	- ## [[SyncThing]]
	  collapsed:: true
		- ### Syncthing is a free, open-source continuous file synchronization program that allows users to securely sync and share files across multiple devices.
			- ~~Install Docker container~~
			- ~~Configure~~
			  collapsed:: true
				- 0-RecipeArchive-bin
				- 1-RecipeArchive-RecipeArchive
				- 2-RecipeArchive-RecipeArchive_Compressed
				- 3-RecipeArchive-Documents
				- 4-RecipeArchive-PDF
				- 5-RecipeArchive-Compressed_ZIP
				- 8-RecipeArchive-All_The_Old_Stuff
				- 9-RecipeArchive-All_The_Old_Stuff_Compressed
			- ### ~~Follow-up: The container is installed and running as a TrueNAS container but I am moving everything over to Dockge so I am going to have to do it all over again.~~
	- ## [[Dockage]]
	  collapsed:: true
		- ### Dockge is a fancy, easy-to-use self-hosted docker compose.yaml stack-oriented manager.
			- NOTES: My initial plan was to exclusively use TrueNAS apps but there are problems:
				- Not everything is available so some Docker container manager is needed.
				- There is no way to backup TrueNAS apps (yes the data can be backed up but the apps can not be backed up).  If I used a Docker container manager the apps are backed up as the Dockage data.
			- ~~Install Docker container~~
-