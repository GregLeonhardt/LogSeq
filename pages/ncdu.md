HowToInstall:: `sudo apt install ncdu`

- # Description:
	- The ncdu command provides a fast and very easy-to-use way to see how you are using disk space on your Linux system.
- # CLI Options:
- ```
  ncdu <options> <directory>
  
  -h,--help                  This help message
  -q                         Quiet mode, refresh interval 2 seconds
  -v,-V,--version            Print version
  -x                         Same filesystem
  -e                         Enable extended information
  -r                         Read only
  -o FILE                    Export scanned directory to FILE
  -f FILE                    Import scanned directory from FILE
  -0,-1,-2                   UI to use when scanning (0=none,2=full ncurses)
  --si                       Use base 10 (SI) prefixes instead of base 2
  --exclude PATTERN          Exclude files that match PATTERN
  -X, --exclude-from FILE    Exclude files that match any pattern in FILE
  -L, --follow-symlinks      Follow symbolic links (excluding directories)
  --exclude-caches           Exclude directories containing CACHEDIR.TAG
  --exclude-kernfs           Exclude Linux pseudo filesystems (procfs,sysfs,cgroup,...)
  --confirm-quit             Confirm quitting ncdu
  --color SCHEME             Set color scheme (off/dark/dark-bg)
  ```
- # Configuration:
	- Ncdu can be configured by placing command-line options in /etc/ncdu.conf or $HOME/.config/ncdu/config. If both files exist, the system configuration will be loaded before the user configuration, allowing users to override options set in the system configuration. Options given on the command line will override options set in the configuration files. The files will not be read at all when --ignore-config is given on the command line.
- # Example:
	- Ignore anything in the /media directory
		- `--exclude /media`
	- Do not follow symbolic links
		- `--no-follow-symlinks`
- # Additional Information:
	- https://dev.yorhel.nl/ncdu/man