# Quickstart

## CLI

### Considerations

- The toolbox favors unix-like operating systems, notably linux and OSX.

- The Clamity CLI supports **zsh** and **bash**. [Read this brief about working
  in a shell environment](docs/shell-environment.md).

- Make sure you have a Clamity supported package manager installed on your
  computer and in your search path (`PATH`). Clamity builds on lots of 3rd party
  software and services and will prompt you to install additional software along
  the way; some via your chosen package manager, other's via vendor provided
  native installation.

  Supported package managers for macos:

  - [macports](https://macports.org) [`port version`]
  - [Homebrew](https://brew.sh) [`brew --version`]

  Supported linux distributions (including their respective package managers):

  - Fedora/CentOS/RedHat **rpm/yum**
  - Ubuntu/Debian **apt/dpkg**

- **[Optional]** Much of clamity's functionality is written in python. It will
  create its own python virtual environment but you'll need to have **python3**
  version **3.10** or greater in your search path. To verify, run the command
  `python3 --version`.

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

1. To get started, type `clamity` for a brief usage or `clamity help` for more
   detail.
