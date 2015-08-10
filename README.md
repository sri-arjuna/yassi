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



Why is the file not named 'yassi'?
----------------------------------

As people like to meet what they already know or expect, i named it **configure** instead, 
generating a script named **make-install** to go conform with the great and powerfull standard '[GNU Autoconf](http://www.gnu.org/software/autoconf/autoconf.html)'.



What does it require?
---------------------
* Shell (/bin/bash and /bin/sh)
* awk, grep, sed
* root access (for default prefix: /usr/local)
* you to create a configure.cfg

As a 'general purpose slash-hammer solution' it expects to be for 'system-wide installations' 
and therefor **make-install** requires root access.



Configure Syntax
----------------

See the latest samples by:

	./configure --sample
	./configure --sample-full

There are 3 **APP** variables:

* APP, which provides the application name for the DATADIR
* APP\_VER, which provides the current version, use (not required) by the **--tarball** option.
* APP\_DIR, change the default (without arguments/options) dir

Each of the _--\*dir_-options provides its name in as variable in CAPS.

So, if you want to place your files in what would be _--bindir=_, simply use _BINDIR=_ within the **configure.cfg**

Please see **--help** output, to figure your target variable.

There are 4 different types of assignments:

* Everything of a directory (**=docs**)
* Single files (**=data/file5.dat**)
* Single directories (**=./somedir**)
* Multiple entries (**="extra/file1.txt ./somedir**)

You even may pass an astrerix to 'limit' the files.

Example:

	MAN1DIR=mans/*.1
	MAN8DIR=mans/*.8

Please be aware to not quote any single entry.

Only quote assignments with multiple items. (asterix (\*) is a single entry and 'must not'! be quoted)



$APP\_dirs.conf:
----------------

To create the **'make-\*'** scripts, a this file is used to save the generated paths.

If your projects provides more than just docs and scripts, this is very much the case, 
then you might want to use:

	doRef=true

As this will save that 'path configuration' used for the project to /etc/$APP.conf, 
so you can refer from your scripts to that file, to know where all the other files are installed.



Specials:
---------

To customize the experience for your users, and after you made sure the (un-)installation script works,
you might want to add your contact info, or a place where people could report bugs about your software.

Simply add:

* BUGS=\* ; Will provide a text to send an email to.
* ISSUE=http://\* ; to provide an URL users can visit to report bugs.


Very often one might need to prepare some files or change them after installation.

If you have such task, consider yourself skilled enough to handle this. ;)

To complete such tasks, **YASSI** provides the use of 3 different arrays:

* PRIOR, things done after writing the REFERENCE file
* POST, things done after installation
* REMOVE, things done during uninstall.

As these are arrays, you will have to assign the values according to BASH syntax, and follow proper escape sequences.

You might want to know that for all the 3 arrays, the variables provided by the **REFERENCE** file shoould be available/usable.

Example:

* PRIOR[0]="echo \"Hello \$USER, you're installing $APP to $BINDIR.\""


Example configurations:

* [yassi-example](https://github.com/sri-arjuna/yassi-example)


And my other projects using this:

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

[Youtube howto](https://youtu.be/KhuariqAL2k), from empty to project to install and uninstall in ~10minutes.

If you like YASSI, you might like [TUI](https://github.com/sri-arjuna/tui) as well.


Bugs:
-----

If you should experience a bug or other issues, please raise an issue on: [https://github.com/sri-arjuna/yassi/issues](https://github.com/sri-arjuna/yassi/issues).