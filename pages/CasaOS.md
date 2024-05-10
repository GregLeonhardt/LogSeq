### Pre-Install:
	- If CasaOS is being installed along side of Open Media Vault (OMV) then the web interface for OMV must be changed as by default both OMV and CasaOS use port 80.
		- System -> Workbench: Port
			- Change from '80' to just about anything else.  '8080' is a good choice.
- ### Install:
	- ``wget -qO- https://get.casaos.io | sudo bash``
	- -OR-
	- ``curl -fsSL https://get.casaos.io | sudo bash``
- ### Uninstall:
	- ``casaos-uninstall``