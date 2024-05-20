- Add a new Shared Folder 'jellyfin' with subdirectories 'movies' and 'tvshows' to store media.
	- ```
	  ---
	  # https://hub.docker.com/r/linuxserver/jellyfin
	  services:
	    jellyfin:
	      image: lscr.io/linuxserver/jellyfin:latest
	      container_name: jellyfin
	      environment:
	        - PUID=1000
	        - PGID=1000
	        - TZ=Etc/UTC
	        - JELLYFIN_PublishedServerUrl=192.168.0.5 #optional
	      volumes:
	        - CHANGE_TO_COMPOSE_DATA_PATH/jellyfin/library:/config
	        - /srv/dev-disk-by-uuid-76237a1f-1655-40ea-be9f-0a4de766bb16/jellyfin/tvshows:/data/tvshows
	        - /srv/dev-disk-by-uuid-76237a1f-1655-40ea-be9f-0a4de766bb16/jellyfin/movies:/data/movies
	      ports:
	        - 8096:8096
	        - 8920:8920 #optional
	        - 7359:7359/udp #optional
	        - 1900:1900/udp #optional
	      restart: unless-stopped
	  
	  ```