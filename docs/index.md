# What's Clamity?

_...because tools separate us from the rest of the animals._

You guessed it, another opionated toolbox. **Clamity** was born from my personal
approach to providing structure, automation and repeatability for software
development through CI/CD pipelines and infrastructure. It has something to
offer all parts of the **SDLC** and **Systems Operations**. Try it. Maybe you'll like
it.

Its primary tool is the `clamity CLI` which blends a custom user interface
interface with documentation in context so my tiny pea-brain doesn't have to
memorize the zillions of ways things work and glue together.

A browser front-ended service is in the ~~planning~~ dreaming stage.

## The Clamity CLI

### Considerations

- The toolbox favors unix-like operating systems, notably linux and OSX.

- The Clamity CLI supports **zsh** and **bash**. [Read this brief about working
  in a shell environment](topics/shell-usage/).

- Make sure you have a Clamity supported package manager installed on your
  computer and in your search path (`PATH`). Clamity builds on lots of 3rd party
  software and services and will prompt you to install additional software along
  the way; some via your chosen package manager, others via vendor provided
  native installation.

  - Supported package managers for macos:
    - [macports](https://macports.org) [`port version`]
    - [Homebrew](https://brew.sh) [`brew --version`]

  - Supported linux distributions (including their respective package managers):
    - Fedora/CentOS/RedHat [**rpm/yum**]
    - Ubuntu/Debian [**dpkg/apt**]

- Much of clamity's functionality is written in python and you're bound to come
  across it sooner or later. It will create its own python virtual environment
  JIT but you'll need to have **python3** version **3.10** or greater in your
  search path. To verify this, run the command `python3 --version`.

### Installation

1. Clone the repo. It's recommended to use the `ssh` protocol as many of the
   `clamity` features rely upon it. To do so, you'll need to add your ssh public
   key to your `github.com` account settings `Github.com > User Menu > Settings > SSH and GPG keys`.
   ```
   cd /my/src
   git clone git@github.com:clamity-toolbox/clamity
   ```
   Cloning via `https` is fine but eventually you'll want to create one or more
   ssh key pair(s) for yourself; `clamity` can help with that too.

1. The `clamity` command is implemented as a shell function so it needs to be
   loaded into your shell. It will _NOT_ be inherited when launching sub-shells
   unless you specifically modify your shell's run-commands file (`~/.zshrc`,
   `~/.bashrc`) to do that. Use the `--quiet` option if you don't want any
   output when loading it.
   ```
   source /my/src/clamity/loader.sh
   ```

1. Consider adding an alias to your shell's run-commands file (`~/.bashrc` or
   `~/.zshrc`) to make it available in all shells you spawn. For example:
   ```
   echo "alias load-clamity='source /my/src/clamity/loader.sh --quiet'" >> ~/.zshrc'
   ```
   Now for all new shells (not your current one), you'll be able to type
   `load-clamity` on the command line to load it.

1. To get started, type `clamity` for a brief usage, `clamity help` for more
   detail or `clamity <command> help` for command-specific info.
   ```
   % clamity
   USAGE
   
   	clamity help
   	clamity { command [sub-command] [options] [[--] positional args]
   
   CLAMITY ACTIONS
   
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
   
   %
   ```

### Include clamity commands in your scripts

If you want to use `clamity` commands in your scripts or programs, use the
`$CLAMITY_ROOT/bin/run-clamity` command. It has the same usage as the `clamity`
shell function. Note that any sub-commaands which mutate the shell's environment
won't survive the command's execution.


## Other Things

### Opinions about Documentation

I consider relevant, well-scoped, easily retrieved documentation a primary
characteristic of any operational environment. Some of the tenets guiding my
choices follow.

- There should be a single source of truth for things. Systems should support
  this philospohy by referring (linking) to them rather than copying or
  restating them.

- Favor context sensitive documentation intermixed with the command interpreter
  for choosing the source of truth. If I'm using the `clamity secrets` command,
  then `clamity secrets help` should have everything I need to complete my
  mission.

- README files living along side code in the repo should be prioritized high
  when choosing a location for a document. In these cases, it should be
  _obvious_ the document is associated with the particular repo (think _user
  guide for an application living with the application code_). We live in a
  repo-centric world.

- Less is more. Assume most people don't like to read (bet ya few make it
  through this page!). Keep it brief and make it as context sensitive as
  possible (think _README files throughout the directory tree of a repo_).

### Contributions

Contributions are welcome with the expectation that you're consistent with the
practices and structure of the toolkit. Create your fork and submit PR's as
desired. And thanks for helping out!
