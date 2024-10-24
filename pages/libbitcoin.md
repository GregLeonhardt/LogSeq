### Documentation:
	- ![A primer for libbitcoin.pdf](../assets/A_primer_for_libbitcoin_1715440804815_0.pdf)
	- ![4. Keys, Addresses, Wallets - Mastering Bitcoin [Book].pdf](../assets/4._Keys,_Addresses,_Wallets_-_Mastering_Bitcoin_[Book]_1715440849244_0.pdf)
	-
- Libbitcoin is a multipurpose bitcoin library targeted towards high end  use. An ideal backend to build fast implementations on top: mobile apps,  desktop clients and server API's. The library places a heavy focus around asychronicity, speed and availability.
- It's enables a big scope for scalability as each component has its own thread pool. By increasing the number of threads for that component the library is able to scale outwards across CPU cores. This are vital as the demands of the bitcoin network grow.
- Libbitcoin can be leveraged with different design patterns depending on the task or application: javascript, python, PHP, Ruby and so on.
	- [[libbitcoin-explorer]]
		- BX exposes over  [80 commands](https://github.com/libbitcoin/libbitcoin-explorer/wiki) and supports network communication with libbitcoin-server or its predecessor Obelisk, and the P2P Bitcoin network. BX is well documented and supports simple and advanced scenarios, including  [stealth] https://wiki.unsystem.net/en/index.php/DarkWallet/Alpha#Stealth)  and  [multisig](https://en.bitcoin.it/wiki/Multisignature) .
		  BX is a rich command line tool for working with Bitcoin. It can be built as a single portable executable for Linux, OSX or Windows and is available for  [download as a signed single executable](https://github.com/libbitcoin/libbitcoin-explorer/wiki/Download-BX)  for each.