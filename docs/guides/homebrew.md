# Homebrew

## Installing Homebrew

!!! warning "Higher privileges needed when installing Homebrew"
    Installing Homebrew itself does need root privileges to be able to create certain
    directories and change their ownership. Later, when installing bottles, root
    privileges are not required anymore except for casks that get installed to
    `/Applications`. Therefore your macOS user account need to be able to adminster
    the computer.

Installing Homebrew is pretty easy by just running the installer. The [Homebrew site](https://brew.sh/)
illustrates this well:

=== "macOS"

    The Xcode Command Line Tools are required to install software with Homebrew. You can install these
    beforehand or let Homebrew ask you to do so. In any case use the command `xcode-select --install`
    to install these.

        /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

=== "Linux"

    On Linux the installation of the requirements works quite differently. Find more details in the
    documentation of [Homebrew On Linux](https://docs.brew.sh/Homebrew-on-Linux).

        /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

## Using Homebrew

The help command shows us the most used commands:

    $ brew --help
    Example usage:
      brew search TEXT|/REGEX/
      brew info [FORMULA|CASK...]
      brew install FORMULA|CASK...
      brew update
      brew upgrade [FORMULA|CASK...]
      brew uninstall FORMULA|CASK...
      brew list [FORMULA|CASK...]

    Troubleshooting:
      brew config
      brew doctor
      brew install --verbose --debug FORMULA|CASK

    Contributing:
      brew create URL [--no-fetch]
      brew edit [FORMULA|CASK...]

    Further help:
      brew commands
      brew help [COMMAND]
      man brew
      https://docs.brew.sh

!!! tip "man brew"
    The manpage of the Homebrew is really a good read especially for terminology
    and details, see `man brew`!

### Updating Homebrew

!!! warning
    Do not confuse the commands update and upgrade!

The command `brew update` will update Homebrew itself and this in principle means
the `brew` command and the local working copy of the repository that holds the formulae
(a `git pull --ff-only` is done). After that command your Homebrew knows the latest
version of all formulae and can tell you those that are newer as what you have installed.
The installed software itself is ***not*** updated.

### Installing software

The command `brew install` will install a software aka formula and all of its dependencies,
i.e `brew install wget`.

There are so called taps, which stands for repositories containg formulae that install
software. By default the taps `homebrew-core` and `homebrew-cask` are already known
and formulae can easily be installed using `brew install FORMULAE`.

* `homebrew-core` contains formulae for software that gets bottled (compiled) and
  distributed
* `homebrew-cask` contains forumlae for software that is already compiled by the
  upstream vendor, i.e. google-chrome, firefox.

One can create its own tap. As an example puppetlabs has its own tap to distribute
puppet, pdk and the like, which means one can tap their tap and install the software
using homebrew though it's not contained in default Homebrew:

    brew tap puppetlabs/puppet
    brew install pdk

### **`brew bundle`**

Manually installing software may be useful on a one by one basis. But imagine
installing all your software after reinstalling your operating system? Do you even
remember what you had/need? Would it be easier to have a list of stuff you need,
that is even versioned? Reinstalling the machine? Easy, reinstall, clone your repo
and run `brew bundle --file Brewfile`. `Brewfile` is an arbitrary text file with
content that my look like this:

    tap "pubppetlabs/puppet"
    brew "findutils"
    brew "wget"
    cask "firefox"
    mas 'Remote Desktop', id: 409907375

The keywords denote how the packages get installed:

line in Brewfile|Command run
---|---
tap "pubppetlabs/puppet"|brew tap puppetlabs/puppet
brew "findutils"|brew install findutils
cask "firefox"|brew install --cask firefox
mas 'Remote Desktop', id: 409907375|mas install 409907375

This file can be created from what you currently have using `brew bundle dump
--file Brewfile`.

See [the `brew bundle` section of the `brew man` output](https://docs.brew.sh/Manpage#bundle-subcommand)
or `brew bundle --help` or [homebrew-bundle] for more details. See [mas-cli] for
the documentation of the mas cli tool.

### Upgrading installed software

Homebrew formulae get frequently updated as their maintainers take care of "their
formulae". This means whenever a certain software is updated, so is the forumlae.
Upgrading the wget package we just installed is done by running the command `brew
upgrade wget`. To upgrade all software that we have so far, just run `brew upgrade`.
Curious beforehand what would be updated? Just run `brew outdated` to see the list
of available upgrades.

### Cleanup the cellar

When upgrade your installed software, Homebrew will keep old versions and the
downloaded packages (tar.gz, dmgs, ...). To get rid of this old stuff you may
run `brew cleanup`.

## Further Stuff

### Scripts

The following script summarizes most of the above tasks into a single script/function.
It will update Homebrew, then check if new version of installed formulae is available
and ask if you upgrade should be carried out. In any case a cleanup run ends the
script. Either add it to its own file, make it executable and put it somewhere in
the path, i.e. ~/bin or define as function in your ~/.bash_profile.

    #!/usr/bin/env bash

    blue=$(tput setaf 33)
    red=$(tput setaf 124)
    reset=$(tput sgr0)

    function prompt_confirm
    {
        while true; do
            printf "\r[ ${yellow}??${reset} ] ${1:-Continue?} [y/n]: ";
            read -r -n 1 REPLY;
            case $REPLY in
                [yY])
                    echo;
                    return 0
                ;;
                [nN])
                    echo;
                    return 1
                ;;
                *)
                    printf " ${red} %s \n${reset}" "invalid input"
                ;;
            esac;
        done
    }

    echo "[ ${blue}..${reset} ] Updating Homebrew";
    brew update;
    out=$(brew outdated);
    if [ ! -z "${out}" ]; then
        echo "[ ${blue}..${reset} ] The following updates are available:";
        echo $out;
        if [ "${1}" = "-f" ] || prompt_confirm "Shall I upgrade all?"; then
            brew upgrade;
            brew cleanup;
        fi;
    fi;
    echo "[ ${blue}..${reset} ] Running brew doctor";
    brew doctor

[homebrew-bundle]: https://github.com/Homebrew/homebrew-bundle
[mas-cli]: https://github.com/mas-cli/mas
