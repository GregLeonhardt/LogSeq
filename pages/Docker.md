# Install
	- Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker `apt` repository. Afterward, you can install and update Docker from the repository.
	- Set up Docker's 'apt' repository.
- # Add Docker's official GPG key:
	- ```
	  sudo apt-get install ca-certificates curl gnupg
	  sudo install -m 0755 -d /etc/apt/keyrings
	  curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
	  sudo chmod a+r /etc/apt/keyrings/docker.gpg
	  ```
	- ## Add the repository to Apt sources:
		- ```
		  echo \
		  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
		  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
		  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
		  ```
			- `sudo apt-get update`
			- ## Note
			  background-color:: red
				- If you use a derivative distro, such as Kali Linux, you may need to substitute the part of this command that's expected to print the version codename:
				  background-color:: red
				- `$(. /etc/os-release && echo "$VERSION_CODENAME")`
				  background-color:: red
				- Replace this part with the codename of the corresponding Debian release, such as 'bookworm'.
				  background-color:: red
	- ## Install the Docker packages.
		- `sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`
	- ## Verify the install
		- Verify that the installation is successful by running the `hello-world` image:
			- `sudo docker run hello-world`
	- # User permissions
	- By default 'root' access is required to run a 'docker' command.  Run the following command to allow the current user permission.
		- `sudo usermod -a -G docker `whoami``
- # Operational Notes
	- https://dockerlabs.collabnix.com/docker/cheatsheet/
- # Packages
- ## [[Dockage]]
- # [[Paperless.ngx]]
- # [[WebTrees]]