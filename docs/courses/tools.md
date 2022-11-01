# Basic Tools

## Homebrew

Working on a desktop OS with a GUI (like I do on macOS), we as sysadmins are
too lazy to move mices (use trackpads) to surf to websites to download
installers to then click through this installer to finally have a small tool or
programm installed. In addition, speaking of macOS, it's not possible to
uninstall a piece of software automatically. This is a manual process done in
Finder.  
Hence we are in need of a good package manager that works like
apt-get/yum found in Linux distructions and that allows us to script things and
install stuff automatically. The most used package manager on macOS these days
is Homebrew. Homebrew is even available on Linux and brings some benefits over
the distribution repositories as it knows a lot more modern tools.

!!! hint
    For Windows users there's an equivalent called [Chocolatey](https://chocolatey.org/).

Find some facts about Homebrew at [Wikipedia](https://en.wikipedia.org/wiki/Homebrew_(package_manager))
Homebrew and its documentation can be found at [https://brew.sh/](https://brew.sh/)

!!! abstract "Task"
    The above should be enough to get you started. Now

    * Install Homebrew
    * Verify its in a working state (see commands available)
    * Install a first CLI tool: wget

## Vim

Next on the plan is [Vim](https://www.vim.org/) the ubiquitous, powerful,
command line-based text editor. Sure the are the GUI-based editors that you are
used to, such as [Visual Studio Code], [Sublime Text] or [Atom]. But, as
previously said, when working on Linux, Vim is already installed. No need to
install "your" text editor first. It's just there there

<https://de.wikipedia.org/wiki/Vim>  
<https://www.vim.org/>

To install Vim, we now have Homebrew. There is a more modern drop-in replacement
called [Neovim] that has Lua support built-in. It works exactly like Vim but has
some other advantages beyond this course, but if you fall in love with Vim, you
should consider switching. Or you already install it now.

!!! abstract "Install Vim or Neovim"
    Now either install `Vim` or `Neovim`. You know how. ;

[Visual Studio Code]: https://code.visualstudio.com/
[Sublime Text]: https://www.sublimetext.com/
[Atom]: https://atom.io/

## Oracle Virtualbox

It is of great value to be able to test as much as possible locally on your machine
that you have always with you. Spinning up a Linux box with the distribution
needed in that moment is priceless. For the sake of our course we will first
make use of Virtual Machines (VM). Later we might also explorer containers with
Docker or Podman.  
The tool of choice to work with virtual machines is VirtualBox (vbox). This tool
is free of charge and very mature and valuable. Other tools include Parallels
Dektop, QEMU, VMware Fusion and others.  

<https://de.wikipedia.org/wiki/VirtualBox>  
<https://www.virtualbox.org/manual/UserManual.html#create-vm-wizard>

!!! abstract "Install VirtualBox"
    Also this tool is installable through Homebrew and split into two packages.
    While the formula `virtualbox` will install the tools, the forumla
    `virtualbox-extension-pack` will install additional features like USB3 and
    others. Install both of them.

## Vagrant

As we do not want by hand (installation wizards, you know), we need another tool
that helps us with managing virtual machines. It allows to define virtual
machines in a text file and then automatically spin the machines up based on
these definitions.

<https://de.wikipedia.org/wiki/Vagrant_%28Software%29>  
<https://learn.hashicorp.com/collections/vagrant/getting-started>

The latter is an invaluable quick start guide. Start your exploration there.
This guide alone will introduce you to a lot of important features and use
cases. Take the time and go through it.

!!! abstract "Install Vagrant"
    As you might have guessed, also Vagrant is installable using Homebrew. Install the
    tool using the formula `vagrant`
