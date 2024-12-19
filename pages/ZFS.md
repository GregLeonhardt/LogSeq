### Commands I use:
	- zpool status
		- Display the operational status for all pools.
	- zpool status {name} -v
		- Display the operational status for storage pool {name} and also any files that have been flagged as corrupted during a scrub operation.
			- NOTE: Corrupted files may be deleted or restored from a backup or snapshot copy.  Upon completion of the delete or restore the file is immediately removed from the list.