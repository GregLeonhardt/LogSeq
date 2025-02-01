### Things I need to do to move all the Synology
	- Copy data from it's current location on Synology to it's new home on TrueNAS.
	- MOUNT TrueNAS shares on Synology
	  | :--- | :--- |
	  | TrueNAS | Status |
	  | DOCKER | DONE |
	  | FTM | DONE |
	  | HOME | DONE |
	  | MEDIA | DONE |
	  | RECIPES | DONE |
	  | SNEAKERNET | DONE |
	  | STK | DONE |
	  | STORA | DONE |
	  | TAPE | DONE |
	- COPY data from Synology to TrueNAS 
	  | :--- | :--- | :---: |
	  | Synology | TrueNAS | Status|
	  | /homes/Belkin | /NetBackup/HOMES/NormaBelkin | 20250201 |
	  | /homes/Donald | /NetBackup/HOMES/DonaldRiggio | 20250201 |
	  | /homes/GregLeonhardt | /NetBackup/HOMES/GregLeonhardt | 20250201 |
	  | /homes/HermanLeonhardt | /NetBackup/HOMES/HermanLeonhardt | 20250201 |
	  | /homes/JK_Leonhardt | /NetBackup/HOMES/JasonLeonhardt | 20250201 |
	  | /homes/steger | /NetBackup/HOMES/JaneEngelcke | 20250201 |
	  | /homes/tom | /NetBackup/HOMES/TomLeonhardt | 20250201 |
	  | /video | /NetBackup/Media/HomeMovies | TODO |
	  | /VideoServer/Movies | /NetBackup/Media/Movies | TODO  | 
	  | /RecipeArchiive | /NetBackup/RECIPES | TODO  |
	  | /STK | /NetBackup/STK | TODO  |
	  | /STORA | /NetBackup/STORA| TODO |
	  | /SneakerNet | /NetBackup/SNEAKERNET | TODO  |
	  |  /Tape-Backup | /NetBackup/TAPE | TODO |
	- Verify the copy data and delete the source files from Synology.
	  | :--- | :--- | :---: |
	  | Compare-A | Compare-B | Status |
	  | /TNS_HOMES/NormaBelkin | /homes/belkin | 20250201|
	  | /TNS_HOMES/DonaldRiggio | /homes/Donald | STARTED|
	  | /TNS_HOMES/GregLeonhardt | /homes/GregLeonhardt | TODO |
	  | /TNS_HOMES/HermanLeonhardt | /homes/HermanLeonhardt | TODO |
	  | /TNS_HOMES/JK_Leonhardt | /homes/JasonLeonhardt | TODO |
	  | /TNS_HOMES/JaneEngelcke | /home/steger | TODO |
	  | /TNS_HOMES/TomLeonhardt | /home/tom | TODO |
	  | /TNS_MEDIA/HomeMovies | /video | TODO |
	  | /TNS_MEDIA/Movies | /VideoStation/Movies | TODO  |
	  | /TNS_MEDIA/TV_Shows | /VideoStation/TV-Shows | TODO |
	  | /TNS_RECIPES | /RecipeArchive | TODO |
	  | /TNS_STK | /STK | TODO |
	  | /TNS_STORA | /STORA | TODO |
	  | /TNS_SNEAKERNET | /SneakerNet | TODO |
	  | /TNS_TAPE | /Tape-Backup | TODO |