# nvm

The best way to install Node.js is to use the Node Version Manager - `nvm`.

https://github.com/creationix/nvm

Note that nvm isn't required - you can download versions and manually install them direct from nodejs.org:

https://nodejs.org/en/download/

But nvm let's you install any version of node, to easily update to a new version and to switch between versions. New releases come out fairly quickly these days and its nice to test out or switch versions.

It lives in your home directory at `~/.nvm` and adds itself as a shell command (bash, zsh etc.)

There is a Windows version here: https://github.com/coreybutler/nvm-windows
Or you can just install Node by downloading it from: https://nodejs.org/en/download/

## installing nvm

To install or update nvm, you can use the install script using cURL:

    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash

or Wget:

    wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash


You'll probably need to make sure your system has a `c++` compiler. For OS X, Xcode will work, for Ubuntu, the `build-essential` and `libssl-dev` packages work.



## usage

```sh
❯ nvm help

Node Version Manager

Usage:
  nvm help                              Show this message
  nvm --version                         Print out the latest released version of nvm
  nvm install [-s] <version>            Download and install a <version>, [-s] from source. Uses .nvmrc if available
  nvm uninstall <version>               Uninstall a version
  nvm use <version>                     Modify PATH to use <version>. Uses .nvmrc if available
  nvm run <version> [<args>]            Run <version> with <args> as arguments. Uses .nvmrc if available for <version>
  nvm current                           Display currently activated version
  nvm ls                                List installed versions
  nvm ls <version>                      List versions matching a given description
  nvm ls-remote                         List remote versions available for install
  nvm deactivate                        Undo effects of \`nvm\` on current shell
  nvm alias [<pattern>]                 Show all aliases beginning with <pattern>
  nvm alias <name> <version>            Set an alias named <name> pointing to <version>
  nvm unalias <name>                    Deletes the alias named <name>
  nvm reinstall-packages <version>      Reinstall global \`npm\` packages contained in <version> to current version
  nvm unload                            Unload \`nvm\` from shell
  nvm which [<version>]                 Display path to installed node version. Uses .nvmrc if available

Example:
  nvm install v0.10.32                  Install a specific version number
  nvm use 0.10                          Use the latest available 0.10.x release
  nvm run 0.10.32 app.js                Run app.js using node v0.10.32
  nvm exec 0.10.32 node app.js          Run \`node app.js\` with the PATH pointing to node v0.10.32
  nvm alias default 0.10.32             Set default node version on a shell

Note:
  to remove, delete, or uninstall nvm - just remove ~/.nvm, ~/.npm, and ~/.bower folders

```


List what versions you currently have installed:

```sh
❯ nvm ls
         v4.2.1
->       v6.9.1
         system
default -> v6.9.1
four -> v4.2.1
stable -> 4.2 (-> v4.2.1) (default)
unstable -> 6.9 (-> v6.9.1) (default)
```

Install 6.9.1:

```sh
❯ nvm install v6.9.1
...
```
