Yet Another Automated Script Installation (yaasi)
=================================================

Why?
----

If you have a script based project you would like to distribute, 
with this simple tool you can handle a most basic installation for GNU/Linux compliant distrobutions.

Inspired by GNU Autoconf & Automake, but quite overhelmed by its power, 
i wrote this to ease the task of writing repeative installation handlers.


How?
----

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
