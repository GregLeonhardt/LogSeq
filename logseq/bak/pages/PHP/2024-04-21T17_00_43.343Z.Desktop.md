# Install PHP
- In this part we will install PHP 5.
	- Step 1. Again open up the Terminal (Applications > Accessories > Terminal).
	- Step 2. Copy/Paste the following line into Terminal and press enter:
		- sudo apt -y install php5 php5-mysql libapache2-mod-php5
- Or sudo apt -y install php php-mysql libapache2-mod-php
	- Step 3. In order for PHP to work and be compatible with Apache we must restart it. Type the following code in Terminal to do this:
		- sudo /etc/init.d/apache2 restart
- # Test PHP
- To ensure there are no issues with PHP let's give it a quick test run.
	- Step 1. In the terminal copy/paste the following line:
		- sudo gedit /var/www/testphp.php
		- This will open up a file called phptest.php.
	- Step 2. Copy/Paste this line into the phptest file:
		- `<!--?php phpinfo(); ?-->`
	- Step 3. Save and close the file.
	- Step 4. Now open you're web browser and type the following into the web address:
		- http://localhost/testphp.php
		- The page should look like this:
			- Congrats you have now installed both Apache and PHP!
- # Installing cURL for PHP
	- `sudo /etc/init.d/apache2 restart`
- # PhpMyAdmin
	- ## Install
	- ```
	  sudo apt-get install -y phpmyadmin
	  sudo vi /etc/apache2/apache2.conf
	  ```
		- Add the following line to the bottom of the file:
			- ```
			  # PHP My Administrator
			  Include /etc/phpmyadmin/apache.conf
			  ```
	- Restart the service to make the changes current:
		- `sudo /etc/init.d/apache2 restart`
- To enable root login:
	- echo "update user set plugin='' where User='root'; flush privileges;" | mysql --defaults-file=/etc/mysql/debian.cnf mysql