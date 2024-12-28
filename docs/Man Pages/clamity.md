```
% clamity  help
USAGE

	clamity help
	clamity { command [sub-command] [options] [[--] positional args]

ABSTRACT
	
	clamity is a collection of tools for software development, CI/CD
	pipeline automation and operations. The CLI provides an abstracted
	interface with contextual help to ease the cognative load that comes
	with the plethora of platform commands.

	The clamity CLI entry point is implemented as a shell function so it
	can manipulate the current shell environment. Use 'run-clamity' if
	including its commands in scripts. Default settings are stored in a
	file and will apply globally to all your shells running clamity
	whereas non-default (local) settings apply solely to the one shell.

	Local settings and data are stored in $CLAMITY_HOME (defaults to
	$HOME/.clamity).

	The clamity user guide can be found at https://user-guide.clamity.com/

CLAMITY COMMANDS

	aws - provides exteneded capabilities to the aws command line utility
	config - manage clamity configuration settings
	context - manage contexts
	env - mutate the shell's environment in useful ways
	help - clamity man page
	os - OS configuration management (includes package manager)
	py - use the clamity python environment (clam-py)
	secrets - secrets store operations
	selfupdate - update clamity and OS packages
	tfm - provides exteneded capabilities to terraform

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

	Bpolean truthiness defines 'false' as an empty string or a case insensitive
	match to anything matching to 'n|no|0|null|none|undefined|undef|f|false'.
	The 'lib/_.sh:_is_false()' shell function is the source of truth for
	truthiness.

SUPPORTED SHELLS

	bash, zsh

ENVIRONMENT VARIABLES
	
	These are set when clamity is loaded. You can pre-define CLAMITY_HOME
	if you don't want it to be '$HOME/.clamity'.

	CLAMITY_ROOT (read-only)
		clamity software directory. This is set when clamity is loaded.

	CLAMITY_HOME
		clamity home dir holds logs, customizations, python virtual env,
		and much more. It is created when clamity is loaded for the first
		time. Unless this variable is set, it will be ~/.clamity.

	CLAMITY_<lower-case-option-name>
		Clamity options are managed using 'clamity config'. Options are
		stored as environment variables prefixed with 'CLAMITY_'.

EXAMPLES
	
	Run 'clamity' or 'clamity help' to get started.

	Update clamity software.

		clamity selfupdate

	Check out the OS environment and configuration.

		clamity os check

	Set a config parameter, in this case CLAMITY_verbose, in the current
	shell only.

		clamity config set verbose 1

	Same as above but set it as a default. It will also have affect for
	all other shells when you run clamity commands. Default settings are
	stored in $CLAMITY_HOME/defaults.env.

		clamity config set default verbose 1
```
