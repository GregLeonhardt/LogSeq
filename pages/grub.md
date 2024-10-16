HowToInstall:: Part of the distributed system.

- # Modify to add Windows
- List available operating systems. Verify that Windows is listed.
	- `sudo os-prober`
- This will add Windows (the new operating system) to the GRUB boot loader.
	- `sudo update-grub`
- # Change Boot Order
	- Edit the configuration file via command:
		- `sudo vim /etc/default/grub`
	- Now, change the line GRUB_DEFAULT=0 to GRUB_DEFAULT=saved and now save the file.
	- To apply the configuration changes you need to run the Update grub command :
		- `sudo update-grub`
	- Finally set a default boot OS simply using the below command:
		- `sudo grub-set-default NUMBER`
- # Change the boot order:
	- Open the terminal with CTRL + ALT + T and execute the command
		- `sudo vim: /etc/default/grub`
		- `enter your password`
	- The configuration file now opens. Change the number at the entry
		- GRUB_DEFAULT.
		- Here, for example, you specify 0 if the default selection in your grub boot loader should be the first entry. For example, for the 5th entry, enter 4 instead.
		- Save the change, close the file and return to the terminal.
		- Now enter the command
			- `sudo grub-mkconfig -o /boot/grub/grub.cfg`
			- and press the Enter key.
		- Then you also execute the command
			- `sudo update-grub`
		- in the Terminal.
	- Finished.