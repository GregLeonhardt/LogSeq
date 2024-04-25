# Install
- ## Step 1: Update Debian packages
	- Before installing any software, it is good practice that all users update their Debian 12 system to the latest packages and dependencies. Open the terminal and run the following command:
	- `sudo apt update`
- ## Step 2: Install MariaDB on Debian 12
	- Once your system is up to date, you can proceed with the MariaDB installation. MariaDB version 10 is available for installation in the default Debian 12 repository. To verify it using this command:
		- `sudo apt show mariadb-server`
	- As we can see, MariaDB 10 is available in the Debian 12 repository. So, enter the following command in the terminal to initiate the installation process:
		- `sudo apt install mariadb-server -y`
- ## Step 3: Secure the MariaDB Installation
	- After the installation completes, it is important to secure your MariaDB installation. To enhance the security of your MariaDB installation, the default security script comes bundled with MariaDB. The below-given command will run a script that performs some security measures:
		- `sudo mariadb-secure-installation`
	- You will be prompted to enter the root password for MariaDB. If you haven't set a password during the MariaDB installation, press Enter to proceed without a password.
	- Setting the root password or using the unix_socket ensures that nobody
	  can log into the MariaDB root user without the proper authorisation.
	- You already have your root account protected, so you can safely answer 'n'.
		- Switch to unix_socket authentication [Y/n]
		- I am not sure which way to go here.  The first try I used the default ‘YES”.
			- Answer: It is working so I guess this is the way to go.
			- The script will ask if you want to set a root password. It is highly recommended to set a strong password for the root user. Type "y" and press Enter to set a new root password, or "n" if you want to keep the existing password.
			- If you choose to set a root password, you will be prompted to enter the new password.
			- Type the password and press Enter. Note that the password won't be visible as you type.
			- The script will then ask if you want to remove anonymous users. It's generally a good practice to remove anonymous users, as they can potentially be a security risk. Type "y" and press Enter to remove the anonymous users, or "n" if you want to keep them.
			- You'll be asked whether to disallow remote root login. It's recommended to disallow remote root login to prevent unauthorized access. Type "y" and press Enter to disable remote root login, or "n" if you want to allow it.
			- The script will prompt you to remove the test database and its associated privileges. It's advisable to remove the test database, as it is not needed in a production environment.
			- Type "y" and press Enter to remove the test database, or "n" if you want to keep it.
			- The next prompt asks if you want to reload the privilege tables to ensure the changes take effect immediately. Type "y" and press Enter to reload the tables.
			- Finally, the script will display a summary of the changes you made. Review the summary to ensure everything is as expected.
			- The mariadb_secure_installation script is now complete, and you have taken important steps to secure your MariaDB installation.
- # Backup and Restore a database:
	- ```
	  **backup:** # mysqldump -u root -p[root_password] [database_name] > dumpfilename.sql
	  **restore:**# mysql -u root -p[root_password] [database_name] < dumpfilename.sql
	  ```
	- ## #crontab
	- You may want the backups to run at a preset interval.  [[crontab]] may be used to schedule your perotic backups.
		- `crontab -e`
	- Append the following to the crontab file:
	- ```
	  # -m- -h- dom mon dow   command
	     0   0   *   *   *    /usr/bin/mysqldump -p{root-passwd} {dBase} > /{dst_dir}/`/bin/date "+\%F_\%H-\%M-\%S"`_{name}.sql
	  ```
- # **Change the DataBase Location**
- To change the location of a MariaDB database on a Debian host server, you'll need to follow these step-by-step instructions:
	- Backup your database: Before making any changes, it's crucial to create a backup of your existing database. This ensures that you have a copy of your data in case anything goes wrong during the process. You can use the mysqldump command to export your database to a SQL file.
	- Stop the MariaDB service: Use the following command to stop the MariaDB service:
		- `sudo systemctl stop mariadb`
	- Move the database directory: Determine the new location for your database directory. Let's say you want to move it to "/new/database/path". Execute the following commands to move the database files:
		- `sudo mv /var/lib/mysql /new/database/path`
	- Update the MariaDB configuration: Open the MariaDB configuration file using a text editor. For example:
		- `sudo vim /etc/mysql/mariadb.conf.d/50-server.cnf`
	- In the configuration file, find the datadir directive, which specifies the current database directory. Modify the directive to reflect the new path. For instance:
		- `datadir = /new/database/path/mysql`
	- Update AppArmor configuration (optional): If your Debian server has AppArmor enabled, you might need to update its configuration to allow MariaDB to access the new database location. Locate the AppArmor configuration file for MariaDB:
		- `sudo vim /etc/apparmor.d/usr.sbin.{mysqld or mariadb}`
	- Modify the file to include the new database path. Look for lines similar to:
	- ```
	  /var/lib/mysql/ r,
	  /var/lib/mysql/** rwk,
	  ```
	- Update them to:
	  ```
	  /new/database/path/ r,
	  /new/database/path/** rwk,
	  ```
	- Start the MariaDB service: Save the changes to the configuration file and exit the editor. Start the MariaDB service using the command:
		- `sudo systemctl start mariadb`
	- Verify the new database location: Confirm that the database is now located in the new directory by checking the MySQL data directory:
		- `sudo mysql -e "SHOW VARIABLES LIKE 'datadir';"`
	- The output should display the new path you configured.
	- Test database functionality: Ensure that the database is functioning correctly by accessing it and performing some basic operations. For example, log in to the
		- `sudo mysql`
	- Then, run some commands like SHOW DATABASES; to verify that your databases are accessible.
	- Congratulations! You have successfully changed the location of your MariaDB database on your Debian host server. Remember to update any relevant configurations or scripts that reference the old database path.
	- ## NOTE:
	  background-color:: red
	- I have toyed with this a little but so far I have not successfully moved the database.
	  background-color:: red
- # Create a database:
	- ```
	  mysql -u root -p
	  
	  mysql> CREATE DATABASE {dBase};
	  mysql> GRANT ALL PRIVILEGES ON {dBase}.* TO {user}@localhost IDENTIFIED BY '{password}';
	  ```
- # Create a user:
	- ```
	  mysql -u root -p
	  
	  mysql> CREATE USER {user}@localhost IDENTIFIED BY '{password}';
	  ```
- # Install Libraries and Header files for C/C++
	- `sudo apt install libmariadb3 libmariadb-dev`