- Configuring and running SyncThing on TrueNAS is relatively simple once you understand that you are working inside a Docker container.  This means that all references to datasets MUST be linked inside the container not the physical dataset or directory on the TrueNAS machine.
	- Edit the SyncThing 'Application Information'
	- Under 'Storage Configuration' and to the right of 'Additional Storage' click the "Add" button.
		- Change 'Type*' to 'Host Path (Path that already exists on the system)'
		- Enter an internal to the container path name for the 'Mount Path*'.
			- For example to share a directory containing photographs you might enter:
				- ``/mnt/photos``
		- Select an existing dataset name in the 'Host Path*'
- Move to the bottom of the page and click 'Update'.
- NOTE: The container will restart to apply the changes.
  background-color:: red
- NOTE: When entering a 'Folder Path' to share in the SyncThing Portal. Enter the 'Mount Path' not the 'Host Path'.
  background-color:: red