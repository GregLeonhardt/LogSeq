# Summary
	- I have convinced myself that the libbitcoin managers have taken the project down.  **Nothing works!**  I suppose the gating factor is that there was a serious security bug discovered.  Anyhow I was able to snag an executable binary from the wayback machine and that is what I will be using until I find it is too old and doesn't work.
	- I am leaving the build notes in place with the hope that the project becomes viable once again.
- # Prerequisites
- The following packages need to be installed before the build can start.
	- ``sudo apt install build-essential autoconf automake libtool pkg-config git g++ clang``
	- `sudo apt install -y libboost1.81-all-dev libboost-chrono1.81-dev`
- # Download and build
	- `cd ~/Downloads`
	- `mkdir libbitcoin-explorer`
	- `cd libbitcoin-explorer`
	- ``wget https://raw.githubusercontent.com/libbitcoin/libbitcoin/version3/install.sh``
	- ``chmod +x install.sh``
	- ``./install.sh --prefix=`pwd`/prefix --with-boost=/usr/local/lib/ --disable-shared``
- # Old Notes that used to work (option-1)
	- ```
	  mkdir libbitcoin
	  cd libbitcoin/
	  
	  wget https://raw.githubusercontent.com/libbitcoin/libbitcoin/version3/install.sh
	  chmod +x install.sh
	  
	  #   ./install.sh --prefix=<InstallDirectory> --build-boost --disable-shared
	  ./install.sh --prefix=`pwd` --build-boost --disable-shared
	  ```
- # Old Notes that used to work (option-2)
	- **NOTE: The only difference I can see between option-1 and option-2 is the directory name**
	  background-color:: yellow
	- ```
	  mkdir bitcoin-explorer
	  cd bitcoin-explorer/
	  
	  wget https://raw.githubusercontent.com/libbitcoin/libbitcoin-explorer/version3/install.sh
	  chmod +x install.sh
	  
	  #   ./install.sh --prefix=<InstallDirectory> --build-boost --build-zmq --disable-shared
	  ./install.sh --prefix=`pwd` --build-boost --disable-shared
	  ```
- # Old Notes that used to work (option-3)
	- TODO This procedure needs to be reformatted or deleted.
	- **# About Libbitcoin
	  
	  The libbitcoin toolkit is a set of cross platform C++ libraries for building bitcoin applications. The toolkit consists of several libraries, most of which depend on the foundational libbitcoin-system library. Each library's repository can be cloned and built using common automake 1.14+ instructions or cmake 3.5+ instructions. There are no packages yet in distribution however each library includes an installation script (described below) which is regularly verified via github actions.
	- # Tools:
	  
	  $ sudo apt install \
	  
	  build-essential \
	  
	  autoconf \
	  
	  automake \
	  
	  libtool \
	  
	  pkg-config \
	  
	  git \
	  
	  g++ \
	  
	  clang
	- # Download:
	  
	  $ cd ~/Download
	  
	  $ git clone [https://github.com/libbitcoin/libbitcoin-explorer.git](https://github.com/libbitcoin/libbitcoin-explorer.git)
	  
	  Or extract the previously downloaded copy.
	  
	  $ cd Download
	  
	  $ unzip ~/Documents/Linux/Install_Packages/libbitcoin-explorer-version3.zip .
	- # Build:
	  
	  $ cd ~/Download/libbitcoin-explorer-version3
	  
	  $ ./install.sh --prefix=/home/greg/Documents/Linux/prefix --build-dir /home/greg/Documents/Linux/build --build-boost --build-zmq --disable-shared
	  
	  clear ; ./install.sh --prefix=/media/greg/BitCoin/LibBitcoin/libbitcoin-explorer-version3 --build-dir /media/greg/BitCoin/LibBitcoin/libbitcoin-explorer-version3/ --build-boost --build-zmq --disable-shared -latomic
	  
	  $ cp ~/Documents/Linux/prefix/bin/bx ~/bin/.
- # libbitcoin Full Build
	- Notes from: https://github.com/libbitcoin/libbitcoin-system/blob/master/README.md
		- # Libbitcoin
			- *The Bitcoin Development Library*
			- [Documentation](https://github.com/libbitcoin/libbitcoin/wiki) is available on the wiki.
			- **License Overview**
				- All files in this repository fall under the license specified in [COPYING](https://github.com/libbitcoin/libbitcoin-system/blob/master/COPYING). The project is licensed as [AGPL with a lesser clause](https://www.gnu.org/licenses/agpl-3.0.en.html). It may be used within a proprietary project, but the core library and any changes to it must be published online. Source code for this library must always remain free for everybody to access.
			- **About Libbitcoin**
				- The libbitcoin toolkit is a set of cross platform C++ libraries for building bitcoin applications. The toolkit consists of several libraries, most of which depend on the base [libbitcoin-system](https://github.com/libbitcoin/libbitcoin-system) library. Each library's repository can be cloned and built using common [automake](http://www.gnu.org/software/automake) 1.14+ instructions. There are no packages yet in distribution however each library includes an installation script (described below) which is regularly verified in the automated build.
		- ## Installation
			- The master branch is a staging area for the next major release and should be used only by libbitcoin developers. The current release branch is version3. Detailed installation instructions are provided below.
				- [Debian/Ubuntu](https://github.com/libbitcoin/libbitcoin-system/blob/master/README.md#debianubuntu)
				- [MacOS](https://github.com/libbitcoin/libbitcoin-system/blob/master/README.md#macos)
				- [Windows](https://github.com/libbitcoin/libbitcoin-system/blob/master/README.md#windows)
		- ### Autotools (advanced users)
			- On Linux and macOS libbitcoin is built using Autotools as follows.
				- ```
				  $ ./autogen.sh
				  $ ./configure
				  $ make
				  $ sudo make install
				  $ sudo ldconfig
				  ```
				- A minimal libbitcoin build requires boost and libsecp256k1. The [libbitcoin/secp256k1](https://github.com/libbitcoin/secp256k1) repository is forked from [bitcoin-core/secp256k1](https://github.com/bitcoin-core/secp256k1) in order to control for changes and to incorporate the necessary Visual Studio build. The original repository can be used directly but recent changes to the public interface may cause build breaks. The `--enable-module-recovery` switch is required.
		- ### Debian/Ubuntu
			- Libbitcoin requires a C++11 compiler, currently minimum [GCC 4.8.0](https://gcc.gnu.org/projects/cxx0x.html) or Clang based on [LLVM 3.5](http://llvm.org/releases/3.5.0/docs/ReleaseNotes.html).
			- Install the [build system](http://wikipedia.org/wiki/GNU_build_system) (Automake minimum 1.14) and git:
			- `sudo apt-get install build-essential autoconf automake libtool pkg-config git`
			- Next download the [install script](https://github.com/libbitcoin/libbitcoin/blob/version3/install.sh) and enable execution:
				- ``wget https://raw.githubusercontent.com/libbitcoin/libbitcoin/version3/install.sh``
				- ``chmod +x install.sh``
			- Finally install libbitcoin with recommended build options:
				- ``./install.sh --prefix=/home/me/myprefix --build-boost --disable-shared``
			- Libbitcoin is now installed in `/home/me/myprefix/`.
		- ### Build Notes for Linux / macOS
			- The [install script](https://github.com/libbitcoin/libbitcoin/blob/version3/install.sh) itself is commented so that the manual build steps for each dependency can be inferred by a developer.
			- You can run the install script from any directory on your system. By default this will build libbitcoin in a subdirectory named `build-libbitcoin` and install it to `/usr/local/`. The install script requires `sudo` only if you do not have access to the installation location, which you can change using the `--prefix` option on the installer command line.
			- The build script clones, builds and installs two unpackaged repositories, namely:
				- [libbitcoin/secp256k1](https://github.com/libbitcoin/secp256k1)
				- [libbitcoin/libbitcoin](https://github.com/libbitcoin/libbitcoin)
			- The script builds from the head of their `version7` and `version3` branches respectively. The `master` branch is a staging area for changes. The version branches are considered release quality.
		- #### Build Options
		- Any set of `./configure` options can be passed via the build script, for example:
			- ``./install.sh CFLAGS="-Og -g" --prefix=/home/me/myprefix``
		- #### Compiling with ICU (International Components for Unicode)
			- Since the addition of [BIP-39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki) and later [BIP-38](https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki) and [Electrum](https://electrum.org/) mnemnoic support, libbitcoin conditionally incorporates [ICU](http://site.icu-project.org/). To use passphrase normalization for these features libbitcoin must be compiled with the `--with-icu` option. Currently [libbitcoin-explorer](https://github.com/libbitcoin/libbitcoin-explorer) is the only other library that accesses this feature, so if you do not intend to use passphrase normalization this dependency can be avoided.
			- ``./install.sh --with-icu --build-icu --build-boost --disable-shared``
		- #### Building ICU and/or Boost
			- The installer can download and install these dependencies. ICU is a large package that is not typically preinstalled at a sufficient level. Using these builds ensures compiler and configuration compatibility across all of the build components. It is recommended to use a prefix directory when building these components.
				- ``./install.sh --prefix=/home/me/myprefix --with-icu --build-icu --build-boost --disable-shared``