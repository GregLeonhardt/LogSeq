### Stuff that needs a solution:
	- DONE Manage [[BtrFS]]
		- I will have to do this manually.
	- DONE Manage snapshot copy
		- Use the '[[snapper]]' package
	- DONE Scrub [[BtrFS]]
		- Use a 'cron' job to perform the scrub.
	- DONE Balance [[BtrFS]]
		- Though not absolutely required this is a good thing to do every once-in-a-while to prevent the over use of some drives while under using the remainder.  Like scrub above, this can be accomplished with the use of BtrFS commands and a cron job.