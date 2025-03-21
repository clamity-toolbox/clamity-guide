```
% clamity selfupdate help
USAGE

	clamity selfupdate help
	clamity selfupdate [-y] [update] [ [--no-pkg-mgr] [--no-backup] [--no-python] | [--me-only] ]
	clamity selfupdate [-y] cron { installed | available | install <cron-template> | remove <cron-template> }

ABSTRACT
	
	Update the clamity software, package managers and packages and all
	matter of software under clamity's umbrella.

SELFUPDATE COMMANDS

	update - update clamity software (default action)

COMMAND OPTIONS
	
	--no-pkg-mgr --no-backup --no-python
		Update the clamity installation without performing the specified task(s).

	--me-only
		Only update the clamity software, do not perform any other tasks.

DESCRIPTION

	update (default action)
		Runs the self update function. The full monty includes:
		  - backup clamity data and software ($CLAMITY_ROOT and $CLAMITY_HOME)
		  - update clamity software (git pull)
		  - update clamity python virtual environment (clam-py update)
		  - update selected package manager (apt, brew, macports, ...) pkgs

	cron
		Manage a simple crontab entry to keep clamity updated. 'installled' lists
		clamity additions currently in your crontab. 'available' lists the
		templates included with clamity which can be installed.

FILES

	Logfiles created by crontab jobs.
		$CLAMITY_HOME/logs/*.cron.*

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

SUPPORTED SHELLS

	bash, zsh

EXAMPLES
	
	Update clamity interactively
		clamity selfupdate

	Update clamity non-interactively without the including the package manager
		clamity selfupdate -y --no-pkg-mgr
```
