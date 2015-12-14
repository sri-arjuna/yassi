Yet Another Simple Script Installer (YASSI)
===========================================

What is it?
-----------

A highly configurable installer based on a single configuration file.


Target Audience
---------------

Developers, packagers and maintainers of projects that are either scripted or no binary executables, or want to have a clean project directory.


Pro & Contra
------------

**Pro**:

1. It only uses a single configuration file
2. Hints to users for optional/recomended commands
3. Provides autodownloader of project if a file or dir is missing
4. Can provide Makefile syntax (for enduser)
5. Last but not least, the installation of a project itself is [very fast!](./screenshots/yassi-is-fast.jpg)!

**Contra**:

1. It comes 'english only' (atm)
2. Tweaking requires know how and where to escape used variables



Why is the file not named 'yassi'?
----------------------------------

As people like to meet what they already know or expect, i named it **configure** instead, 
generating a script named **make-install** to go conform with the great and powerfull standard '[GNU Autoconf](http://www.gnu.org/software/autoconf/autoconf.html)'.

Please, do use '[GNU Autoconf](http://www.gnu.org/software/autoconf/autoconf.html)' if you must compile your project!



Requirements
------------

* Shell (/bin/bash)
* gawk, grep, sed, which



Install YASSI
-------------

Please see docs/INSTALL.md for details.



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
