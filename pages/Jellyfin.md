### compose.yaml
	- ```
	  services:
	    jellyfin:
	      image: jellyfin/jellyfin:latest
	      container_name: jellyfin
	      env_file: .env
	      #environment:
	      # - PUID=568
	      # - PGID=545
	      # - TZ=America/Denver
	      # - JELLYFIN_PublishedServerUrl=http://192.168.0.14:32004
	      volumes:
	        - /mnt/volume1/Docker/Jellyfin/Cache:/cache:rw
	        - /mnt/volume1/Docker/Jellyfin/Config:/config:rw
	        - /mnt/volume1/Media:/Media:ro
	      ports:
	        - 32004:8096
	      #     - 8920:8920 #Optional - Https webUI (you need to set up your own 
	      #       certificate).
	      #     - 7359:7359/udp #optional - Allows clients to discover Jellyfin 
	      #       on the local network.
	      #     - 1900:1900/udp #optional - Service discovery used by DNLA and 
	      #       clients.
	      restart: unless-stopped
	  networks: {}
	  
	  ```
- ### .env
	- ```
	  PUID=568
	  PGID=545
	  TZ=America/Denver
	  #        Set the autodiscovery response domain or IP address, include 
	  #        http(s)://.
	  JELLYFIN_PublishedServerUrl='http://192.168.0.14:32004'
	  ```