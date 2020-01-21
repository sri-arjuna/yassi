How to use YASSI
================

I will focus on the syntax of YASSI,
as I exepect you as an author to know where the files you created belong.



Influence the \-\-help output
-----------------------------

There are the **APP_\*** variables of which only the **APP_NAME** is required,
all others are optional. However, it is recomended to use **APP_VERSION** as well,
to avoid possible version confusions.

If you want to reach out to the users of the script,
you can provide your contact information with the **AUTHOR-\***
and/or the **MAINTAINER_\*** variables avilable.

You can even provides **MAILLIST_{BUGS,NEWS}** and **BUGTRACKER** information.
**Note:** If you use **APP_GIT** variable,
it will add information to raise an _issue_ on github in case of bugs.



Handle project dependencies:
----------------------------

Sooner or later you have projects that depend on other things as well.
Depending on the situation, this could be _'must be this'_ or _'one of those'_.
Or it just is required to compile info,html or manpages

Use **REQS[app]** to assign a list of applications/commands/packages your project nees to run.
Now, sometimes projects support manpages or other kind of documention and
in most cases, actualy creating them is optional.

Regardless, if you want to do so, some commands/packages are required.
This is where **REQS[make]** comes in, assign a list of packages required
during any possible _make\*_ execution.

Sometimes you just want the enduser to know that your project has optional features too.
For example, my "NASA Image of the day", while it requires 'feh' to set an image as background,
it can also resize the image - if the user has installed 'ImageMagick'.
So that is what I would then add to the list for the **REQS[opt]** entry.

It may also happen that you provide handlers, in which case just one command per function is required.
To handle such dependencies, assign a list of related commands for each **REQS_ONE[id]**



Assign files and folders to targets
-----------------------------------

Now lets talk about the most used basics.

Obviously you want to install something. But, how does it come?
A single file, a single folder with all files or several folders and subfolders?

Dont you worry, this will be easy!
Well, unless you use REGEX, but that is optional and I will not cover this here.


Say, you want to install a single file to **/bin**, naturaly, you would use:

    BINDIR=myfile


If you have multiple files, all inside a dir named 'bin', it would be:

    BINDIR=bin


However, lets say you have other files you want to provide.
Lets call them templates and screenshots.

    SHAREDDIR="./templates ./screenshots"


This would install both directories themself and all their content to /usr/share/APP_NAME/

All files found during expanding directories will get listed individualy for the **make-unstall** script to avoid 'accidents'.



Make things happen!
-------------------

You need hardcoded paths in your script?
No problem!

YASSI automaticly creates **$APP_NAME**\_dirs.conf which can be used during the **MAKE** stages.

You could even make it install that file to the targets /etc by setting **doRef=true**

But how do you do / use that? Well, it could look like:

    MAKE[0]="scripts/prepare.sh"
    MAKE[1]="scripts/gen-myfile.sh > ./myfile"


Just to be complete, the _${APP_NAME}\_dirs.conf_ file would be sourced by the _gen-myfile.sh_.
In identical ways you can use PRIOR[@] POST[@] REMOVE[@] DISTCLEAN[@] CLEAN[@] IGNORE[@] UNINSTALL[@]

These features are only required if you need to generate additional files during the make process.



Make documentions!
------------------

This can be easy, if you came prepared young padawan!

Lets say you have prepared some texi files, awesome!

Lets make some INFO and HTML pages from that:

    # This will generate the make-doc-{info,html} file
    DOCS[info]=docs/tex/$APP_NAME.texi
    DOCS[html]=docs/tex/$APP_NAME.texi

    # This will actualy copy the generated files during the installation
    INFODIR=docs/tex/\*.info
    HTMLDIR=docs/tex/\*.html


Thats all you'll need to do.
