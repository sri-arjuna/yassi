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

As this will save that 'path configuration' used for the project to /etc/$APP.conf or $HOME/.local/etc, 
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

* PREPARE, things done during ./configure
* PRIOR, things done after writing the REFERENCE file
* POST, things done after installation
* REMOVE, additional files created during PRIOR
* CLEAN, remove files created during PREPARE

As these are arrays, you will have to assign the values according to BASH syntax, and follow proper escape sequences.

You might want to know that for all the 3 arrays, the variables provided by the **REFERENCE** file shoould be available/usable.

Example:

* PRIOR[0]="echo \"Hello \$USER, you\'re installing $APP to $BINDIR.\""

