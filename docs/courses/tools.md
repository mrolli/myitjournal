# Basic Tools

## Homebrew

Working on a desktop OS with a GUI (like I do on macOS), we as sysadmins are too lazy to move mices (use trackpads)
to surf to websites to download installers to then click through this installer to finally have a small tool or
programm installed. In addition, speaking of macOS, it's not possible to uninstall a piece of software automatically.
This is a manual process done in Finder.  
Hence we are in need of a good package manager that works like apt-get/yum found in Linux distructions and that allows
us to script things and install stuff automatically. The most used package manager on macOS these days is Homebrew.
Homebrew is even available on Linux and brings some benefits over the distribution repositories as it knows a lot more
modern tools.

!!! hint
    For Windows users there's an equivalent called [Chocolatey](https://chocolatey.org/).

Find some facts about Homebrew at [Wikipedia](https://en.wikipedia.org/wiki/Homebrew_(package_manager))
Homebrew and its documentation can be found at [https://brew.sh/](https://brew.sh/)

!!! abstract "Task"
    The above should be enough to get started. Now

    * Install Homebrew
    * Verify its in a working state (see commands available)
    * Install a first CLI tool: wget

## Vim

Auf jeden Fall wäre die nächste Etappe, den Texteditor Vim zu installieren:
Wissenswertes/Historie zu Vim: https://de.wikipedia.org/wiki/Vim

Für das installieren von Vim haben wir ja jetzt Homebrew. ;-)

Dann habe ich dir versprochen, noch einen "GUI-Texteditor" zu empfehlen. Es sind sogar zwei. Beide per Homebrew installierbar:
- Sublime Text (https://www.sublimetext.com/)
- Atom (https://atom.io/)

Beide sind prima. Matthias benutzt z.B. Atom. Ich würde wohl mal mit Atom beginnen, aber beide testen. Den, den du nicht behalten willst, kannst du dann dank Homebrew wieder deinstallieren. Du sollst ja den erstmal nur nutzen, solange du im Vi noch nicht sattelfest bist.

## Oracle Virtualbox

Um virtuelle Maschine lokal auf deinem Macbook zu haben, hat sich Virtualbox als nützlich erwiesen. Das ist von Oracle und ist kostenlos. Alternativ gäbe es noch Dinge wie Parallels Desktop, VMWare Fusion und andere. Wir nutzen Virtualbox. Auch dieses kannst du per Homebrew installieren. Die Formeln heissen virtualbox und virtualbox-extension-pack.

## Vagrant

Da wir virtuelle Maschinen nicht manuell installieren wollen (du weisst, installation wizards....) benötigen wir noch ein Tool, welches uns hier hilft: Vagrant. Die Installation des Tools geht natürlich auch wieder per Homebrew:

https://de.wikipedia.org/wiki/Vagrant_%28Software%29
https://learn.hashicorp.com/collections/vagrant/getting-started

Letzteres ist ein Quickstart-Giude, mit dem du bereits eine virtuelle Maschine erstellst und darin sogar schon einen Linux-Webserver installierst. Allein dieses Getting-Started Tutorial wird dich mind. einen Tag beschäftigen.
