Yet Another Simple Script Installation (yassi)
==============================================


What does it do?
----------------

Inspired by GNU Autoconf & Automake, but got quite overhelmed by its power, 
so i wrote this to ease the task of writing repeative installation handlers.

It is a simple installer, based upon a simple config file usage.
Therefor, it only places the files, you have to take care previously about their permission and preparation.



What is it for?
---------------

It is for small projects, or script based projects that do not require to be complied for a specific architecture, 
or contain just plain text files or only multimedia binaries.



Why is the file not named 'yaasi'?
----------------------------------

As people like to meet what they already know or expect, i named it **configure** instead, 
generating a script named **make-install**



What does it require?
---------------------
* Shell (/bin/bash and /bin/sh)
* root access (for default prefix: /usr/local)

As a 'general purpose slash-hammer solution' it expects to be for 'system-wide installations' 
and therefor **make-install** requires root access.



Config configure
----------------

Make a file called **configure.cfg** with this example content, and place it along with **configure** in your **project root dir**.

	APP=project-name
	BINDIR=bin
	DOCDIR=README.md
	DATADIR="./templates ./samples"
	doRef=true


First line **APP=project-name** is required to get the proper naming for the path structures, such as **/usr/share/$APP**.

The following **BINDIR,DOCDIR,DATADIR** show all the features available as of now.
(*To define what files or folders shall me installed somewhere, simply write its option-name in capitals,
followed by either a file or folder name.*)

Install a file:

	DOCDIR=README.md

One may pass multiple entries, in fact, passing a folder name will 'expand' to its content.

Install all files of a folder:

	BINDIR=bin	

Install multiple folders (these will actualy copy the folder, not just its content):

	DATADIR="./templates ./samples"


To create a reference file, which contains the assigned paths:

	doRef=true

Which then will write the file **$APP\_ref.conf** which will be automaticly installed to **SYSCONFDIR (/etc/$APP.conf)**.



Syntax:
-------

Assinging files and paths to \*DIR variables follows simple rules.

* If there is just one entry - no quotes
* If there are multiple entries - quotes!
* Every path is expanded to its content, unless it starts with **./**

If you need want some real uses of my own **configure.cfg**'s:

* [connect](https://github.com/sri-arjuna/connect)
* [dev-scripts](https://github.com/sri-arjuna/dev-scripts)



Make-files
----------

After you did run something like:

	./configure --prefix=/usr

you will see, there are 3 new files in the path, all starting by **make-**.

* make-distclean, removes the just created files
* make-install, installs the project/package
* make-uninstall, removes the installed project/package


Other:
------

[Youtube howto](http://youtu.be/6JUPkuCY1UE), from empty to project to install and uninstall in ~10minutes
If you like YASSI, you might like [TUI](https://github.com/sri-arjuna/tui) as well.