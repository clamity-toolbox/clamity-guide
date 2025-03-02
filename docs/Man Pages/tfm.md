```
% clamity tfm help
USAGE

	clamity tfm { vars | smart-import | record-results } [-reconfigure] [tfm-options]
	clamity tfm apply [--no-commit] [tfm-options]
	clamity tfm common { report | update [mine] | new-root <state-group> <module-name> }
	clamity tfm settings { show | [un]set aws-profile [profile] }
	clamity tfm cicd complete [-reconfigure]
	clamity tfm debug [ on | off ]  # (un)sets the 'TF_VAR_debug' env var
	clamity tfm { terraform-cmd-and-args }

ABSTRACT
	
	This facility provides extended features for managing terraform through
	the CI/CD lifecycle, hopefully making repetative tasks and configurations
	simpler to manage.

	Use the 'clamity tfm' command as if it were an alias for the 'terraform'
	command. It intercepts custom sub-commands (extensions), passing the rest
	through to 'terraform' directly so 'clamity tfm state list' is identical
	to 'terraform state list'. Some terraform commands are intercepted and
	the command line passed to 'terraform' modified to accomodate global settings
	for things like state management. For example, 'clamity tfm init' will add the
	'-backend-config=xxx' arg for the appropriate config before passing through
	to 'terraform init'.

	To make these extensions useful, you must agree to manage your terraform root
	modules in a particular way.

TFM COMMANDS

	apply - overload the TF apply sub-command to record results
	cicd - CI/CD processing
	common - verify & sync tf code common to all root modules
	init - overload the TF init sub-command to support access to the state
	record-results - saves state to STATE.md and output to OUTPUT.json
	settings - set properties for the repo
	smart-import - Assist importing live resources into a root module's state
	state-report - summarize resource deployments by state group
	vars - display terraform environment variables

COMMAND OPTIONS
	
	-reconfigure
		Force -reconfigure with terraform init.

	--no-commit
		When running 'apply', don't commit and push changes to the repo.

SUB-COMMANDS

	cicd {complete}
		An interface into various CI/CD pipeline processes. 'complete' will
		execute a 'terraform plan' (and 'init' if need be) on all root modules
		in sequence.

	common
		The 'common' subcommand syncs the code residing in the common/ directory
		across all participating root modules. You can opt-in on a file-by-file
		basis simply by keeping a copy of the file with the same name within
		the root module directory. This	mechanism solves the problem whereby
		terraform code, at the outer-most level, requires specific attributes
		and properties for the deployment, such as provider definitions which
		often result in duplicated code.

	record-results
		Saves state listing to STATE.md and output to OUTPUT.json.

	settings
		You can set an aws_profile by state_group to use locally which when running
		terraform commands. This is if you don't want to manage it with the
		AWS_PROFILE env variable.

	smart-import
		System for reading resource data and importing it into state. This requires
		customizations specific to each terraform root module and is typically
		not used unless terraforming an existing installation.

	state-report
		List resource deployments (state list) by state group.

	vars
		Display variables associated with terraform (TF_*, TFM_*, CLAMITY_TFM_*).

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

FILES
    TFM_REPO_ROOT/.clamity/config/settings.sh
		Configuration settings for the repo. This file should be committed.

    TFM_REPO_ROOT/.clamity/config/module-sequence.sh
		Script to provides the sequence in which root modules should be applied
		allowing for intra-module dependencies. This should be executed from
		within TFM_REPO_ROOT. This file should be committed.

    TFM_REPO_ROOT/.clamity/config/state-resource-prefix.sh
		Provides the resource prefix and region required for identifying backend
		state resources when creating new root modules. This should be executed
		from within TFM_REPO_ROOT. This file should be committed.

	TFM_REPO_ROOT/.clamity/local/settings.sh
		Configuration settings for the repo which should _not_ be committed.
		Examples include your desired AWS_PROFILE values by state group.

ENVIRONMENT VARIABLES
	
	TFM_REPO_ROOT
		Full path to and including this repo's root.

	TFM_POST_COMMIT
		Controls execution of post-apply commit and push. Valid values are
		'commit-only' (won't push), 'none' (won't commit or push), or null
		(default) which will commit and push.

EXAMPLES
	
	List your root modules

		A 'terraform.tf' file in a directory under $TFM_REPO_ROOT/roots/
		designates a module root.

		clamity tfm common

	Initializing Pre-canned State Configurations

		To facilitate custom strategies for managing backends and states,
		a '.tfm.sh' file, in the root's directory, may be used to setup the
		apporpriate parameters. It's a good habbit to initialize your state
		using this tool. Add '-dryrun' if you want to see what it would do.

		clamity tfm init
```
