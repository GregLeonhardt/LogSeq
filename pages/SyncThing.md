### config.yaml
	- ```
	  version: "3"
	  services:
	    syncthing:
	      image: syncthing/syncthing
	      container_name: syncthing
	      hostname: TrueNAS-SyncThing
	      environment:
	        - PUID=568
	        - PGID=545
	        - TZ=Etc/America-Denver
	      volumes:
	        - /mnt/volume1/Docker/SyncThing/Config:/config
	        - /mnt/volume1/Recipes:/mnt/Recipes
	        - /mnt/volume1/home/GregLeonhardt/Documents:/mnt/Documents_Greg
	      ports:
	        - 32007:8384
	        - 22000:22000/tcp
	        - 21027:21027/udp
	      #    network_mode: host
	      restart: unless-stopped
	  networks: {}
	  
	  ```