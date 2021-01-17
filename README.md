***Pool modified for Digibyte coin.***

*** Initially download the digibyte blockchain from http://cryptochainer.com/dir/

* Digibyte blockchain download: `wget -c http://147.135.10.45/blockchains/current/DigiByte_blockchain.zip`

* Ensure the file (digibyte.conf) exists in your digibyted blockchain directory prior to launching digibyted.
		
		Example directory path: (/opt/blockchain/digibyte/skein/.digibyte)
		
		Example digibyted startup: (./digibyted /opt/blockchain/digibyte/skein/.digibyte)
		
`Contents of digibyte.conf:`

		server=1
		rpcuser=USERNAME
		rpcpassword=PASSWORD
		algo=skein
		listenonion=0
		listen=1
		daemon=1
		gen=0
		onlynet=IPv4
		rpcworkqueue=32
		rpcthreads=96
		rpcallowip=127.0.0.1
		rpcbind=127.0.0.1
		rpcport=14024
		port=12026
		deprecatedrpc=accounts
		prune=550
		
* Wait for the Digibyte daemon (digibyted) to be fully synced prior to launching p2pool.


P2pool installation with pypy -- Linux
---------------------------------------

Copy and paste the following commands one paragraph at a time into a bash shell in order to install p2pool on Linux.


		sudo apt-get update

		sudo apt-get install pypy pypy-dev pypy-setuptools gcc build-essential git net-tools

		cd /opt
		wget https://bootstrap.pypa.io/ez_setup.py -O - | sudo pypy
		sudo rm setuptools-*.zip

		cd /opt
		wget https://pypi.python.org/packages/source/z/zope.interface/zope.interface-4.1.3.tar.gz#md5=9ae3d24c0c7415deb249dd1a132f0f79
		tar zxf zope.interface-4.1.3.tar.gz
		cd zope.interface-4.1.3/
		sudo pypy setup.py install
		cd ..
		sudo rm -r zope.interface-4.1.3*

		cd /opt
		wget https://pypi.python.org/packages/source/T/Twisted/Twisted-15.4.0.tar.bz2
		tar jxf Twisted-15.4.0.tar.bz2
		cd Twisted-15.4.0
		sudo pypy setup.py install
		cd ..
		sudo rm -r Twisted-15.4.0*

		cd /opt
		git clone https://github.com/farsider350/p2pool-dgb-scrypt-350.git
		cd p2pool-dgb-scrypt-350
		cd digibyte_subsidy
		sudo pypy setup.py install
		cd ..
		cd litecoin_scrypt
		sudo pypy setup.py install    


Running P2Pool:
-------------------------
To use P2Pool, you must be running your own local digibyted. For standard configurations, using P2Pool should be as simple as:

		For Zen Server
		pypy run_p2pool.py --net digibyte
		
To make your node accessible from the internet, open the following ports on your router (both the worker port and peer-2-peer port): 
* Worker Port = `5025`
* Peer-2-Peer Port = `5024`
* Confirm ports are listening: `netstat -na | egrep '5024|5025'` 

Run for additional options: `pypy run_p2pool.py --help`


Donations towards further development:
-------------------------
DGB: D8WsfBwbYX6BTpaBL3hbc4k5pL4Def6sSh
