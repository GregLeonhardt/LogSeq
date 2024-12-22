### Commands I use:
	- zpool status
		- Display the operational status for all pools.
	- zpool status {pool_name} -v
		- Display the operational status for storage pool {name} and also any files that have been flagged as corrupted during a scrub operation.
			- NOTE: Corrupted files may be deleted or restored from a backup or snapshot copy.  Upon completion of the delete or restore the file is immediately removed from the list.
	- zpool clear {pool_name}
		- If a device is taken offline due to a failure that causes errors to be listed in the zpool status output, you can clear the error counts with the zpool clear command. If a device within a pool is loses connectivity and then connectivity is restored, you will need to clear these errors as well.