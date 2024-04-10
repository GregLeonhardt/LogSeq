- **NOTE: These instructions are very old.  They may work or they may only be the foundation for something that works.  In any event use them with caution!
	- Also: They have been ported from another note system and need formatting.  I don't want to take the time to do the formatting for something that may not work.  If I ever build a #WordPress system, I'll figure it out then.
- Install [[MariaDB]]
- Install [[Apache (httpd)]]
- Install [[PHP]]
- ## **Install WordPress**
- Step 1: Prerequisites installation
	- `apt-get install php5-mysql mysql-server`
- Step 2: Download and Decompress Wordpress
- We start by downloading a latest version of Wordpress and decompressing it into /var/www/wordpress 
  
  cd /var/www
  wget http://wordpress.org/latest.zip
  unzip latest.zip
  
  At this point all files should be within /var/www/wordpress directory.
- Step 3: Apache Configuration
  
  In this step we will create a new apache site called wordpress, enable it and disable default apache website.
  
  cd /etc/apache2/sites-available
  sed 's/www/www\/wordpress/g' default > wordpress
  a2ensite wordpress
  a2dissite default
  
  Restart apache to apply all changes:
  
  /etc/init.d/apache2 restart
- Step 4: Creating Wordpress database
  
  Next, we will need to create a MySQL database to be used with our Wordpress installation:
- Username: wordpress
- Password: wordpress
- Database name: wordpress
  
  mysql -p
  Enter password:
  Welcome to the MySQL monitor.  Commands end with ; or \g.
  Your MySQL connection id is 39
  Server version: 5.1.41-3ubuntu12.10 (Ubuntu)
  
  Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
  
  mysql> CREATE DATABASE wordpress;
  Query OK, 1 row affected (0.00 sec)
  
  mysql> CREATE USER 'wordpress'@'localhost' IDENTIFIED BY 'wordpress';
  Query OK, 0 rows affected (0.00 sec)
  
  mysql> GRANT ALL PRIVILEGES ON wordpress.* to wordpress@localhost;
  Query OK, 0 rows affected (0.00 sec)
  
  mysql> quit
  Bye
- Step 5: Creating wp-config.php
  
  To continue a Wordpress installation we need to create a wp-config.php file to accommodate all Wordpress configuration needs. Use following lines to insert database name, database user and password into wp-config.php file.
- # cd /var/www/wordpress/
- # cp wp-config-sample.php wp-config.php
- # sed -i 's/database_name_here/**wordpress**/' wp-config.php
- # sed -i 's/username_here/**wordpress**/' wp-config.php
- # sed -i 's/password_here/**wordpress**/' wp-config.php
- # chmod 600 wp-config.php
  
  OR use text editor of your choice to supply wp-config.php with correct information:
  
  // ** MySQL settings - You can get this info from your web host ** //
  
  /** The name of the database for WordPress */
  
  define('DB_NAME', '**wordpress**');
  
  /** MySQL database username */
  
  define('DB_USER', '**wordpress**');
  
  /** MySQL database password */
  
  define('DB_PASSWORD', '**wordpress**');
  
  /** MySQL hostname */
  
  define('DB_HOST', 'localhost');
  
  Ensure that apache have access to wordpress installation files. If this is your local system make sure that www-data owns of all files:
- # chown -R www-data.www-data /var/www/wordpress