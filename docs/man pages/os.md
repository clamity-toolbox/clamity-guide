```
% clamity os help
USAGE

	clamity os { <sub-command> } [options]

ABSTRACT
	
	The OS command is for configuring and managing your local host's
	operating system.

OS COMMANDS

	check - probe OS for config & environment info
	cron - work with cron
	pkg - abstracted package management
	pm - power management

COMMAND OPTIONS
	
	--opt-a
		boolean yes or no

	--opt-name <name>
 		the name of the thing you specifed using --opt-name.

COMMON OPTIONS

	-d, --debug
		Debug mode provides additional, lower-level output (CLAMITY_debug=1). Debug
		messages are sent to stderr.

	-n, --dryrun
		Allows for execution of a script withot causing an underlying change to whatever
		data the script affects. It is up to each script to determine what that means.
		Some scripts do not support dryrun and will terminate immediately if it's enabled
		(CLAMITY_dryrun=1).

	-of, --output-format { json | text | csv }
		Specifies format of output where applicable (CLAMITY_output_format). Defaults
		to json.

	-or, --output-redirection { none | log }
		Sets up output redirection. 'none' leaves stdout and stderr untouched (this is
		the default setting). 'log' captures both stdout and stderr to one log file and
		sets CLAMITY_logfile to the full path and name of the logfile, using that value
		if already set (CLAMITY_output_redirection="{none | log}").

	-q, --quiet
		Suppress (or minimize) all reporting except warnings and errors (CLAMITY_quiet=1).

	-v, --verbose
		Enable extra reporting (CLAMITY_verbose=1). Includes printing the commands being
		run under the hood to stdout.

	-y, --yes
		Disables interactive mode in which commands that prompt for confirmation before
		doing things will automatically get answered with 'yes' (CLAMITY_yes=1).

ENVIRONMENT VARIABLES
	
	CLAMITY_os_preferred_pkg_mgr
		Supported package managers: brew | port | yum | apt

EXAMPLES
	
	This is one way to it
		ls /tmp
```
