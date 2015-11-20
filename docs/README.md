YASSI 1.0
=========

What is it?
-----------

In _one_ word: **an installer**

Which is an acronym for: Yet Another Simple Script Installer


Target Audience
---------------

If you have projects that do not need to be compiled, but might need small preparations.
As example, if you have a scripted project that requires some small preparations like texinfo or txt2man (but not limited to these).

It aims to become an easy to use installer for non-binary-executable (arch-independant) projects.


Why is the file not named 'yassi'?
----------------------------------

As people like to meet what they already know or expect, i named it **configure** instead, 
generating a script named **make-install** to go conform with the great and powerfull standard '[GNU Autoconf](http://www.gnu.org/software/autoconf/autoconf.html)'.

Please, do use '[GNU Autoconf](http://www.gnu.org/software/autoconf/autoconf.html)' if you must compile your project!


Pro & Contra
------------

**Pro**:

1. It only uses a single configuration file
2. It is highly configurable
3. Its usage/behaviour is similar as with GNU Autotools (to the enduser)
4. It provides 2 different sample configurations (./configure --sample|--sample-full)
5. Once **./configure --prefix=/usr** is executed, it generates 4 files:
	* make-distclean, removes the just created files
	* make-install, installs the project/package
	* make-uninstall, removes the installed project/package
	* ${APP}\_dirs.conf, provides all the system dirs used, and can be copied to SYSCONFDIR automaticly
6. Last but not least, the installation itself is ALOT faster!
	

**Contra**:

1. It comes 'english only'
2. Tweaking requires know how and where to escape used variables


Requirements
------------

* Shell (/bin/bash and /bin/sh)
* awk, grep, sed


Installing YASSI
----------------

First of all, you need to get the files, either by...

**GIT**:

	cd ~/Projects
	git clone git clone https://github.com/sri-arjuna/yassi.git yassi
	
**CURL**:
	
	curl -Lo yassi.zip https://github.com/sri-arjuna/yassi/archive/master.zip
	unzip yassi
	mv yassi-master yassi && rm -f yassi.zip
	

Then you need to apply it to your project

	cd ~/Projects/ProjectA
	cp ../yassi/configure .
	./configure --sample > configure.cfg
	${EDITOR:-vi} configure.cfg
	
Or if you want to read the info file, actualy install it by itself.

	cd ~/Projects/yassi
	./configure --prefix=$HOME/.local
	./make-install
	info yassi

To do an uninstallation:

	cd ~/Projects/yassi
	./make-uninstall
	

Examples
--------

These are some free script projects of mine using YASSI:

* [yassi-example](https://github.com/sri-arjuna/yassi-example)
* [VHS (Video Handler Script)](https://github.com/sri-arjuna/vhs)
* [connect](https://github.com/sri-arjuna/connect)
* [dev-scripts](https://github.com/sri-arjuna/dev-scripts)


Learn more
----------

By reading: [docs/USAGE.md](docs/USAGE.md)

Or watching a [Youtube howto](https://youtu.be/KhuariqAL2k), from an empty to project to install and uninstall in ~10minutes.

If you like YASSI, you might like [TUI](https://github.com/sri-arjuna/tui) as well.


Bugs:
-----

If you should experience a bug or other issues, please raise an issue on: [https://github.com/sri-arjuna/yassi/issues](https://github.com/sri-arjuna/yassi/issues).