# 2024-04-04
	- This just isn't working reliably.  I made several changed on the desktop and pushed all of them.  They are not showing up on the laptop.  **AND THEY ARE NOT IN THE REPOSITORY**
		- This "MAY" be a procedural problem.  The push was failing because there were changes at the repository.  The tool couldn't push any new changes until the changes at the repository were pulled.
- ### NOTES:
  background-color:: yellow
	- It looks like the 'get', 'commit', and 'check status' cycle are completely manual.  In other words if you don't check for changes you won't know there are any in the repository resulting in stuff not being in sync.
		- OOPS.  I guess it will look from time-to-time.  I just don't know what the interval is.
	- If you save a file (ctl-s) [which isn't needed] the GIT plugin will push the changes.
	- To clone the repository:
		- git clone https://github.com/GregLeonhardt/LogSeq.git
- …or create a new repository on the command line
  
  ```
  echo "# LogSeq" >> README.md
  git init
  git add .
  git commit -m "first commit"
  git branch -M main
  git remote add origin https://github.com/GregLeonhardt/LogSeq.git
  git push -u origin main
  ```
- …or push an existing repository from the command line
  
  ```
  git remote add origin https://github.com/GregLeonhardt/LogSeq.git
  git branch -M main
  git push -u origin main
  ```
- …or import code from another repository
  
  You can initialize this repository with code from a Subversion, Mercurial, or TFS project.