Installation of YASSI
=====================

No installation required. (But is available)
All that is required to do is to copy ./bin/configure to your project root and run:

	./configure --sample-full > configure.yassi

This will write a full template with all options listed, but commented out.
Once you changed the configure file according to:

	./configure --manpage
	
All your endusers will then have to do, is either of the two example lines:

	./configure --prefix=$HOME/local ; ./make ; ./make-install-all
	./configure ; make && sudo make install


Install YASSI
-------------

Be aware that this would be a local-only solution and is not recomend!

However, this method is suggested:

	su
	cd /usr/src
	git clone http://https://github.com/sri-arjuna/yassi
	cd yassi
	
	./configure --prefix=/usr
	./make
	./make-install
	

Remove YASSI
------------

It is as simple as the installation:

	su
	cd /usr/src/yassi
	
	./make-uninstall
	
	cd ..
	rm -fr yassi
