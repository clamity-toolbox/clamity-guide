```
% clamity config help
USAGE

	clamity config list
	clamity config { set | unset } [default] {config-opt} [value]
	clamity config show [defaults]

ABSTRACT
	
	config manages your clamity settings. When you set an option, you
	define it in your current shell only. When you set it as a default,
	you set it in your current shell _and_ in a local file that will be
	seen by all active and future clamity terminal shells.

	Unsetting a variable affects both the current shell and, if default
	is specified, removes the setting from the local file. Note that
	unsetting a variable will _not_ affect other active shells.

CONFIG COMMANDS

	list - list config variables
	set - set a config variable
	show - report env and default settings
	unset - unset config variable

DESCRIPTIONS

	list
		list common config options.

	set ['default'] <config-opt> <value>
		Sets a configuration option <config-opt>. For a list of _some_
		config options, run 'clamity config list'. Options aren't managed
		centrally. The 'default' keyword stores the setting and applies to
		all current shells using clamity. Otherwise, the setting is only
		in the environment of the current terminal shell.

	show ['defaults']
		Print the options. 'default' shows the options from the persistent
		settings file. otherwise it lists the options set in the environment.

	unset ['default'] <config-opt>
		Unsets an option (see set).

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

BOOLEAN EVALUATION

	Boolean truthiness defines 'false' as an empty string or a case insensitive
	match to anything matching to 'n|no|0|null|none|undefined|undef|f|false'.
	Convention for setting booleans is to set them to a value of 1.

	The 'lib/_.sh:_is_false()' shell function is the source of truth for
	truthiness.

SUPPORTED SHELLS

	bash, zsh

EXAMPLES
	
	Set verbose on by default (CLAMITY_verbose)
		clamity config set default verbose 1

	Set debug for my session only (CLAMITY_debug)
		clamity config set debug 1
```
