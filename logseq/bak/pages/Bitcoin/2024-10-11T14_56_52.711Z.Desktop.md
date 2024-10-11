# Download and Install
	- Open a terminal window on your Debian system. You can usually find the terminal application in the Applications menu or by using the keyboard shortcut Ctrl+Alt+T.
	- Update your package list and upgrade existing packages by running the following command:
		- `sudo apt update && sudo apt upgrade`
	- Visit the Bitcoin Core website at: https://bitcoin.org/en/download.
	- Locate the appropriate download link for the Debian version of Bitcoin Core. Make sure you choose the correct architecture (32-bit or 64-bit) based on your system.
	- Right-click on the download link and select "Copy link address" to copy the URL.
	- In the terminal, navigate to the directory where you want to download the Bitcoin Core installation package. You can use the cd command to change directories. For example, to navigate to the Downloads directory, you can use:
		- `cd ~/Downloads`
	- Download the Bitcoin Core installation package using the wget command followed by the copied URL. For example:
		- `wget <paste-the-copied-url-here>`
	- Once the download is complete, verify the integrity of the downloaded file by comparing its SHA256 checksum with the one provided on the Bitcoin Core website. You can find the checksum on the download page of the website.
	- Open a web browser and visit the SHA256 checksum verification page at https://bitcoin.org/bin/verify. Follow the instructions on that page to calculate the SHA256 checksum of the downloaded file.
	- Compare the calculated checksum with the one provided on the Bitcoin Core website. If they match, proceed to the next step. If they don't match, delete the downloaded file and repeat steps 4 to 9.
	- Extract the Bitcoin Core installation package by running the following command:
		- `tar xzf bitcoin-<version>-x86_64-linux-gnu.tar.gz`
			- Replace <version> with the actual version number of the downloaded package.
	- Move into the extracted Bitcoin Core directory by using the following command:
		- `cd bitcoin-<version>/bin`
	- Install the Bitcoin Core binaries to the system's executable path by executing the following command:
		- `sudo install -m 0755 -o root -g root -t /usr/local/bin/ bitcoin-26.0/bin/*`
	- Bitcoin Core is now installed on your Debian system. You can start the software by typing bitcoin-qt in the terminal, or you can launch it from the Applications menu.
	- Please note that these instructions assume a basic familiarity with the Linux command line. Make sure to double-check the version numbers and adjust the commands accordingly if there are updates available on the Bitcoin Core website.
		- ## Executables:
		- TODO : The following list is incomplete.
		- ```
		  bitcoin-qt
		  bitcoind
		  ```
- # Configuration
	- [bitcoin.conf](../assets/bitcoin_1718998632363_0.conf)
- # AutoStart
	- Create or modify file /etc/systemd/system/bitcoind.service:
		- `sudo vi /etc/systemd/system/bitcoind.service`
			- [bitcoind.service](../assets/bitcoind_1710817614789_0.service)
	- ## Management Commands:
	- ```
	  sudo systemctl start bitcoind
	  $ sudo systemctl status bitcoind
	  $ sudo systemctl stop bitcoind
	  $ sudo systemctl enable bitcoind
	  $ sudo systemctl disable bitcoind
	  ```
- # Install from Source
  Write step-by-step instructions for installing bitcoin core from bitcoin.org on a debian system.
- # [[libbitcoin]]