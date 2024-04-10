HowToInstall:: Part of the distributed system.

- # How to run hourly
	- Linux, you have to hate it to love it.  The steps below **DO NOT WORK**, or at least the files don't appear to ne updating.  after running the 'reenable' command it shows a couple of linked files.  Both of these files still show daily run cycles.  (I didn't wait for the clock to get to the top of the hour.)  The following command moves when logrotate is run from daily to hourly.
		- ``sudo mv /etc/cron.daily/logrotate /etc/cron.hourly/logrotate``
	- It is now running hourly but both changes are in place.  Maybe some time down the road I'll experiment some more.
- # How to run hourly
	- On Debian Bullseye (and maybe other modern systemd based systems) logrotate is handled by a systemd timer which runs once a day. To change the run frequency of logroate to a hourly frequency, you have to override the default logrotate.timer unit.
	- Execute `systemctl edit logrotate.timer` and insert the following overrides:
		- ```
		  ### Editing /etc/systemd/system/logrotate.timer.d/override.conf
		  ### Anything between here and the comment below will become the new contents of the file
		  
		  [Unit]
		  Description=Daily rotation of log files
		  Documentation=man:logrotate(8) man:logrotate.conf(5)
		  
		  [Timer]
		  OnCalendar=hourly
		  AccuracySec=1m
		  Persistent=true
		   
		  [Install]
		  WantedBy=timers.target
		  
		  ### Lines below this comment will be discarded
		  ```
	- Then run `systemctl reenable --now logrotate.timer` to activate the changes.
	- The empty `OnCalender` option resets the previous defined values.
	- The default `logroate.timer` has set the `AccuracySec` option to one hour. Unfortunately resetting it with an empty value is not possible so it has to be set to one minute manually.