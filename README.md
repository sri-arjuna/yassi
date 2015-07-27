Yet Another Automated Script Installation (yaasi)
=================================================


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


Config configure
----------------

To apply this to your project, simply place 'configure' in your projects root directory.

All its required configuration is done in a new file **configure.cfg** your create.

First of all, you need to name it with:

	APP=project-name

But be aware that what you set for APP will be used for path structures, such as /usr/share/$APP.

Now regarding the actual installation.

As a 'general purpose slash-hammer solution' it expects to be for 'system-wide installations' 
and therefor **make-install** requires root access.

To define what files or folders shall me installed somewhere, simply write its option-name in capitals,
followed by either a file or folder name.

One may pass multiple entries, in fact, passing a folder name will 'expand' to its content.

Install a file:

	DOCDIR=README.md

Install all files of a folder:

	BINDIR=bin	

Install multiple folders:

	DATADIR="./templates ./samples"


To create a reference file, which contains the assigned paths:

	doRef=true

Which then will write the file **$APP\_ref.conf** which will be automaticly installed to SYSCONFDIR (/etc).


So, the final example could look like:

	APP=project-name
	BINDIR=bin
	DOCDIR=README.md
	DATADIR="./templates ./samples"
	doRef=true
