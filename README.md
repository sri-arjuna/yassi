Yet Another Simple Script Installation (yassi)
==============================================


What does it do?
----------------

Inspired by GNU Autoconf & Automake, but quite overhelmed by its power, 
i wrote this to ease the task of writing repeative installation handlers.

Which i found quite challenging and annoying to place so many files in so many directories.

It is a simple installer, based upon a simple config file usage.


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


Make-files
----------

After you did run something like:

	./configure --prefix=/usr

you will see, there are 3 new files in the path, all starting by **make-**.

* make-distclean, removes the just created files
* make-install, installs the project/package
* make-uninstall, removes the installed project/package
