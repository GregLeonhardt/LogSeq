# Install
- To start off we will install Apache.
	- Open up the Terminal (Applications > Accessories > Terminal).
	- Copy/Paste the following line of code into Terminal and then press enter:
		- `sudo apt -y install apache2`
	- The Terminal will then ask you for your password, type it and then press enter.
- # Test
	- To make sure everything installed correctly we will now test Apache to ensure it is working properly.
	- Open up any web browser and then enter the following into the web address:
		- `http://localhost/`
		- You should see a folder entitled apache2-default/. Open it and you will see a message saying "It works!" , congrats to you!
- # Reverse Proxy
	- ## Enabling Necessary Apache Modules
		- Apache has many modules bundled with it that are available but not enabled in a fresh installation. First, we’ll need to enable the ones we’ll use in this tutorial.  Specifically, we will use:
			- mod_proxy
				- the main proxy module Apache module for redirecting connections; it allows Apache to act as a gateway to the underlying application servers.
			- mod_proxy_http
				- which adds support for proxying HTTP connections.
		- These modules are installed by running the following commands:
			- `sudo a2enmod proxy`
			- `sudo a2enmod proxy_http`
	- ## Configuration
		- The WEB server needs directions on what to do with the HTTP requests that arrive.  This is done by modifying file '/etc/apache2/sites-available/000-default.conf' with the following information.
			- ServerName:
				- Defines the domain name associated with a server. You may either configure it on the Internet via DNS or set it up locally via the /etc/hosts file, if you want to reach your server by the associated domain name.
			- ServerAlias:
				- Allows you to define additional names that are going to be accepted by the server.
			- ServerAdmin:
				- The contact email address that the server includes in error messages that are returned to the client.
			- ErrorLog:
				- Sets the name of a file that Apache uses to store any errors it encounters.
			- CustomLog:
				- Sets the name of a file that Apache uses to log client requests to the server.
			- ProxyPass:
				- Maps remote servers into the space of the local server.Defines the target address for traffic redirection.
			- ProxyPassReverse:
				- A proxy server not only receives requests but can also forward response packets back to the client. ProxyPassReverse command rewrites the original location, content-location and uri HTTP response headers of the back-end server with the proxy server’s information. This is essential to avoid bypassing the reverse proxy and isolate back-end servers from the Internet.
			- ProxyRequests:
				- Prevents the Apache HTTP server from being used as a forward proxy and makes it more secure. The ProxyRequests command should usually be set to off when using ProxyPass.
	- ## Example:
		- ```
		  <VirtualHost *:80>
		  	ServerName {site name as entered by client}
		  	ServerAlias www.{site name as entered by client}
		  	ServerAdmin postmaster@site1.com
		  	ErrorLog ${APACHE_LOG_DIR}/error.log
		  	CustomLog ${APACHE_LOG_DIR}/access.log combined
		  	ProxyPass / http://{hostname or IP address}:{port}/
		  	ProxyPassReverse / http://{hostname or IP address}:{port}/
		  	ProxyRequests Off
		  </VirtualHost>
		  ```
		- ```
		  <VirtualHost *:80>
		  	ServerName 508r.dyndns.org:mealie
		  	ServerAlias www.508r.dyndns.org:mealie
		  	ServerAdmin postmaster@site1.com
		  	ErrorLog ${APACHE_LOG_DIR}/error.log
		  	CustomLog ${APACHE_LOG_DIR}/access.log combined
		  	ProxyPass / http://192.168.0.10:7225/
		  	ProxyPassReverse / http://192.168.0.10:7225/
		  	ProxyRequests Off
		  </VirtualHost>
		  ```
- ## Restart:
	- The apache2 WEB server needs to be restarted for the above changes to take effect.
		- `sudo systemctl restart apache2`