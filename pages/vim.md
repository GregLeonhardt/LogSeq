HowToInstall:: `sudo apt get vim -y`

- # Configure:
	- Edit or create file "~/.vimrc" and append the following:
	- ```
	  " Enable Syntax highliting
	  syntax on
	  
	  " Set the color scheme
	  colorscheme murphy
	  
	  " Number of visual spaces per TAB
	  set tabstop=4
	  
	  " Number of spaces in tab when editing
	  set softtabstop=4
	  
	  " Tabs are spaces
	  set expandtab
	  
	  " Show line numbers
	  set number
	  
	  " Highlight current line
	  set cursorline
	  
	  " Highlight matching [{()}]
	  set showmatch
	  ```
- NOTE: The .vimrc file used a quote (") for comments.