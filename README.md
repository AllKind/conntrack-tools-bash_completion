conntrack-tools-bash_completion
==========

Programmable completion specification for conntrack-tools (netfilter).
This package includes completions for conntrack, conntrackd and nfct.

http://www.netfilter.org/projects/conntrack/index.html

Project home:

http://sourceforge.net/p/conntrack-tools-bash-compl

https://github.com/AllKind/conntrack-tools-bash_completion

Programmable completion allows the user, while working in an interactive shell,
to retrieve and auto-complete commands, their options, filenames, etc.
Pressing [TAB] will complete on the current word, if only one match is found.
If multiple completions are possible, they will be listed by hitting [TAB] again.


Requirements
==========

bash version 4 or greater.
The bash completion package version 2.0 or greater is recommended.
https://github.com/scop/bash-completion


Features all
==========

If the bash completion package is present, and the version includes the
**_init_completion()** function, completion on variables and redirection
is available in addition. Otherwise only option completion is fully supported.


Features conntrack
==========

Protocol and service names are retrieved from /etc/{protocols,services} and offered for completion.

Numeric protocol names are recognized and their options will be made available.


Features nfct
==========

Support for nfct is a bit limited. Retrieval of object names is not yet supported.


Installation
============

Quote from bash-completion README:

	Install it in one of the directories pointed to by
	bash-completion's pkgconfig file variables.  There are two
	alternatives: the recommended one is 'completionsdir' (get it with
	"pkg-config --variable=completionsdir bash-completion") from which
	completions are loaded on demand based on invoked commands' names,
	so be sure to name your completion file accordingly, and to include
	for example symbolic links in case the file provides completions
	for more than one command.  The other one which is present for
	backwards compatibility reasons is 'compatdir' (get it with
	"pkg-config --variable=compatdir bash-completion") from which files
	are loaded when bash_completion is loaded.

	For packages using GNU autotools the installation can be handled
	for example like this in configure.ac:

	 PKG_CHECK_VAR(bashcompdir, [bash-completion], [completionsdir], ,
	   bashcompdir="${sysconfdir}/bash_completion.d")
	 AC_SUBST(bashcompdir)

	...accompanied by this in Makefile.am:

	 bashcompdir = @bashcompdir@
	 dist_bashcomp_DATA = # completion files go here

	For cmake we ship the bash-completion-config.cmake and
	bash-completion-config-version.cmake files. Example usage:

	 find_package(bash-completion)
	 if(BASH_COMPLETION_FOUND)
	   message(STATUS
		 "Using bash completion dir ${BASH_COMPLETION_COMPLETIONSDIR}")
	 else()
	   set (BASH_COMPLETION_COMPLETIONSDIR "/etc/bash_completion.d")
	   message (STATUS
		 "Using fallback bash completion dir ${BASH_COMPLETION_COMPLETIONSDIR}")
	 endif()

	 install(FILES your-completion-file DESTINATION
	   ${BASH_COMPLETION_COMPLETIONSDIR})

For backwards compatibility it is still possible
to put it into ~/.bash_completion or /etc/bash_completion.d/.

Tip: To make tab completion more handsome put the following into either /etc/inputrc or ~/.inputrc:

     set show-all-if-ambiguous on

This will allow single tab completion as opposed to requiring a double tab.

     set page-completions off

This turns off the use of the internal pager when returning long completion lists.


