# Laptop

Laptop is a script to set up an OS X laptop (or desktop) for development.

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages based on what is already installed on the machine.

## Requirements

Laptop has been tested on:

* [OS X Mavericks (10.9)](https://itunes.apple.com/us/app/os-x-mavericks/id675248567)
* [OS X Yosemite (10.10)](https://www.apple.com/osx/)

Older versions may work but aren't regularly tested. Bug reports for older versions are welcome.

## Install

Download, review, then execute the script:

```sh
curl --remote-name https://raw.githubusercontent.com/massimoksi/laptop/master/mac
less mac
sh mac 2>&1 | tee ~/laptop.log
```

## Debugging

Your last Laptop run will be saved to `~/laptop.log`.
Read through it to see if you can debug the issue yourself.
If not, copy the lines where the script failed into a [new GitHub Issue](https://github.com/massimoksi/laptop/issues/new) for me.
Or, attach the whole log file as an attachment.

## What it sets up

* [Homebrew] for managing operating system libraries
* [Git] for version control
* [Bash completion] for fast typing on Terminal
* [Rbenv] for managing versions of Ruby
* [Ruby Build] for installing Rubies
* [Ruby] stable for writing general-purpose code
* [Bundler] for managing Ruby libraries

[Homebrew]: http://brew.sh/
[Git]: https://git-scm.com/
[Bash completion]: https://bash-completion.alioth.debian.org/
[Rbenv]: https://github.com/sstephenson/rbenv
[Ruby Build]: https://github.com/sstephenson/ruby-build
[Ruby]: https://www.ruby-lang.org/en/
[Bundler]: http://bundler.io/

It should take less than 15 minutes to install (depends on your machine).

## Customize in `~/.laptop.local`

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.
This repo already contains a `.laptop.local` you can use to get started.

Download the sample file to your computer.

```sh
curl -o $HOME/.laptop.local https://raw.githubusercontent.com/massimoksi/laptop/master/laptop.local
```

Write your customizations such that they can be run safely more than once.
Laptop functions such as `fancy_echo`, `brew_install_or_upgrade`, and `gem_install_or_update`
can be used in your `~/.laptop.local`.
See the [wiki](https://github.com/thoughtbot/laptop/wiki) for more customization examples.

For example:

```sh
#!/bin/sh

brew_install_or_upgrade 'git-flow'
brew_install_or_upgrade 'hub'
brew_install_or_upgrade 'git-extras'
brew_install_or_upgrade 'carthage'
brew_install_or_upgrade 'cloc'
brew_install_or_upgrade 'uncrustify'
brew_install_or_upgrade 'ffmpeg'

brew cleanup -s

gem_install_or_update 'cocoapods'
gem_install_or_update 'jazzy'
```

## Credits

This laptop script is based on and inspired by [thoughtbot's laptop](https://github.com/thoughtbot/laptop) script.

## License

Laptop is © 2011-2015 thoughtbot, inc.
It is free software, and may be redistributed under the terms specified in the [LICENSE] file.

[LICENSE]: LICENSE
