- Download and install ubuntu-mate
  
  * USER: 'hyperbackup'
  
  * Install to [[LVM]]
  
  -----------------------------------------------------------------------------------------------------
- login as root:
- `apt update`
- `apt upgrade -y`
- `apt install -y vim rsync`
  -----------------------------------------------------------------------------------------------------
  Configure RSYNC:
- `vim /etc/default/rsync`
- ```
  CHANGE        RSYNC_ENABLE=false
  TO            RSYNC_ENABLE=true
  ```
- -----------------------------------------------------------------------------------------------------
- `vim /etc/rsyncd.conf`
- Insert the following:
- ```
  [backup]
  path = /home/hyperbackup/hyperbackup
  comment = Synology HYPER-BACKUP
  read only = false
  timeout = 60
  auth users = hyperbackup
  secrets file = /etc/rsyncd.secrets
  ```
- -----------------------------------------------------------------------------------------------------
- `vim /etc/rsyncd.secrets`
- Insert the following:
	- ```
	  hyperbackup:{password}
	  ```
- -----------------------------------------------------------------------------------------------------
	- `chmod 640 /etc/rsyncd.secrets`