```
% clamity context help
USAGE

	clamity context { help | show }
	clamity context data-pack { installed | set [<data-pack>] | clear | install-git <data-pack-url-via-git> | remove <data-pack> | update | fetch [prop] }

ABSTRACT
	
	Many clamity functions operate in a given context. For example, if you're
	working with AWS resources the AWS SDK access credentials and region will
	determine the endpoint and role applied to the task at hand. Clamity is
	aware of some context types and can let you switch between them.

	Known context types:
	- AWS
	- Git based data packs

CONTEXT COMMANDS

	data-pack - manage data packs
	show - report contexts

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

EXAMPLES
	
	Install some data packs.
		clamity context data-pack install-git git@github.com:teamvortexsoftware/infra-data-dev
		clamity context data-pack install-git git@github.com:teamvortexsoftware/infra-data-prod
```
