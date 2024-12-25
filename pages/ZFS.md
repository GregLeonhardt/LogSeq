### Commands I use:
	- zpool status
		- Display the operational status for all pools.
	- zpool status {pool_name} -v
		- Display the operational status for storage pool {name} and also any files that have been flagged as corrupted during a scrub operation.
			- NOTE: Corrupted files may be deleted or restored from a backup or snapshot copy.  Upon completion of the delete or restore the file is immediately removed from the list.
	- zpool clear {pool_name}
		- If a device is taken offline due to a failure that causes errors to be listed in the zpool status output, you can clear the error counts with the zpool clear command. If a device within a pool is loses connectivity and then connectivity is restored, you will need to clear these errors as well.
	- zpool scrub -e {pool_name}
		- Only scrub files with known data errors as reported by `zpool` `status` `-v`. The pool must have been scrubbed at least once with the [**head_errlog**](https://openzfs.github.io/openzfs-docs/man/master/8/zpool-scrub.8.html#head_errlog) feature enabled to use this option. Error scrubbing cannot be run simultaneously with regular scrubbing or resilvering, nor can it be run when a regular scrub is paused.