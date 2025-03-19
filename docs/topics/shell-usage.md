# Working in a Shell

The **clamity CLI** and other functions run within a **shell environment**.
There's a myriad of ways to setup and use your shell environments. These
observations and principals have served me well.

## You should know...

- Your **login shell** is your parent environment under which everything you do
  will operate. This includes applications run from launchpad on a mac or gnome
  on a linux workstation, as well as the environment you get when you open a
  terminal window.

- Your `~/.bash_profile` (`~/.zprofile`) and `~/.bashrc` (`~/.zshrc`) files are
  used to setup your shell environment to your liking. The **profile** file is
  executed by your host operating system's login sequence when you login whereas
  the **run-commands** files (`~/.*rc`) are executed every time you launch a
  shell.

- A good general rule is to set things in your **profile** intended to be
  inherited by sub-shells and applications (for example, exported environment
  variables) while settings not inherited (for example aliases or shell
  functions) but which you always want available to you, would be placed in the
  **run-commands** file.

- _Here's the rub_... the more you do to customize your login shell (mother of
  all sub-shells) the more conflict you risk as the variety of things you do
  increases. If you set `export MY_LICENSE_KEY=123` in your `~/.zprofile`, that
  variable will be defined for _every_ application you run and _every_ sub-shell
  you launch. Maybe that's what you want or maybe that's a problem. You must
  decide for yourself.

- _That said..._ good automation relies upon structure and completeness so
  defining things at a global level (like in your login shell) tend to be
  counter productive to ensuring consistency between individuals or in varying
  contexts.

- One other good principal to live by is that mutating a shell for a different
  purpose by removing things is generally difficult to do well and therefore not
  an ideal pursuit. Consider shells ephemeral. Delete them when you're done with
  whatever task you were doing and start the next task with a new shell.

## My recommendation for Operators

Operators tend to require maximum flexibility to accomodate the numerous
contexts in which commands run. Keep your login shell as vanilla as possible
while making modifying your shell's environment on-demand, simple.

- Define `aliases` in your **run-commands** file to easily modify your
  environment for specific tasks. For example, a `load-brew` alias could be used
  to add **homebrew** to your search path or `load-clamity` can source the
  **clamity CLI** into your shell.

- Even something as foundational as adding a package manager to your search path
  might be something you want to do outside your login shell. For example, when
  you install `macports` it will add it to your search path in your login shell.
  Likewise, when you load `homebrew` it will define functions and variables in
  your login shell. You may want the ability to switch package managers or
  change the priority in your search path on a shell-by-shell (task-by-task)
  basis. Or you may want a shell environment that doesn't include either.

- Keep your **profile** sparse, maybe even empty. Remember that any vars you
  define and export here will be visible to everyhing you do.

Here's how I handle shell setup on my mac:

```sh
% cat ~/.zprofile
export HISTCONTROL=ignorespace
export SOME_TOKEN_I_WANT_SET_IN_ALL_SHELLS="token-value-goes-here"


% cat ~/.zshrc
# Load Toolkits
function __add_to_path { echo "$PATH" | grep -q "$1" || export PATH="$PATH:$1"; }
# load clamity
alias load-clamity='source $HOME/src/clamity-toolbox/clamity/loader.sh'
# use macports packages (priority)
alias load-macports='echo "$PATH" | grep -q /opt/local/bin || export PATH="/opt/local/bin:/opt/local/sbin:$PATH"'
# use homebrew packages. Also the postgres and mysql command line utilities
alias load-homebrew='eval "$(/opt/homebrew/bin/brew shellenv)"; __add_to_path /opt/homebrew/opt/libpq/bin; __add_to_path /opt/homebrew/opt/mysql-client/bin'
# NVM node version manager
alias load-nvm='source /opt/local/share/nvm/init-nvm.sh; __add_to_path ./node_modules/.bin'

# Setup Development Environments
# use macports packages. Also inclues nvm and clamity.
alias load-dev-port='load-macports; load-nvm; load-clamity --quiet'
# use homebrew packages. Also inclues nvm and clamity.
alias load-dev-brew='load-homebrew; load-nvm; load-clamity --quiet'
# Use homebrew packages first, then macports packages. Also inclues nvm and clamity.
alias load-dev-1='load-homebrew; load-macports; load-nvm; load-clamity --quiet'

# Uncomment _only one_ of these if you want that environment in place for all shells.
# load-dev-1
# load dev-brew
```

## My recommendation for Developers

Set things up like operators but call an alias in your `~/.*rc` file to load the
environment you always work with (uncomment _only one_ of the last `load-dev-*`
lines above).
