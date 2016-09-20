# Laptop

Laptop is a script to set up an OS X laptop (or desktop) for development.

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages based on what is already installed on the machine.

## Requirements

Laptop has been tested on:

* OS X Mavericks (10.9)
* OS X Yosemite (10.10)
* OS X El Capitan (10.11)

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

## Create your laptop files

At the end of the script, Laptop looks for configuration files inside your `~/.laptop` directory.
Put your customizations there in files with a `laptop` extension.
This repo already contains a `demo.laptop` you can use to get started.

Download the sample file to your computer.

```sh
curl -o $HOME/.laptop/demo.laptop https://raw.githubusercontent.com/massimoksi/laptop/master/demo.laptop
```

Write your customizations such that they can be run safely more than once.
Laptop functions such as `fancy_echo`, `brew_install_or_upgrade`, and `gem_install_or_update`
can be used.
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

gem_install_or_update 'cocoapods'
gem_install_or_update 'jazzy'
```

## Credits

This laptop script is based on and inspired by [thoughtbot's laptop](https://github.com/thoughtbot/laptop) script.

## License

Laptop is © 2011-2015 thoughtbot, inc.
It is free software, and may be redistributed under the terms specified in the [LICENSE] file.

[LICENSE]: LICENSE
