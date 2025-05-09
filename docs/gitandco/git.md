# Git

## Learning Git

The following three videos by David Mahler are a decent introduction to Git
version control system and teach you the key concepts of Git in a illustrative
way. Runtime is 30m each for a total of 1.5h. I wish I started to learn Git this
way back then. :stuck_out_tongue_winking_eye:

<!-- markdownlint-disable -->
[![Core Concepts](https://img.youtube.com/vi/uR6G2v_WsRA/0.jpg)](https://www.youtube.com/watch?v=uR6G2v_WsRA)  
[![Branching and Merging](https://img.youtube.com/vi/FyAAIHHClqI/0.jpg)](https://www.youtube.com/watch?v=FyAAIHHClqI)  
[![Remotes](https://img.youtube.com/vi/Gg4bLk8cGNo/0.jpg)](https://www.youtube.com/watch?v=Gg4bLk8cGNo)  
<!-- markdownlint-restore -->

In addition, the below book, the visual overview of the most used Git commands
and lastly the visual playground below are helpful too. And.. Git's very good
documentation as the one source of truth as reference.

* [Git Reference](https://git-scm.com/docs)
* [Pro Git Book](https://git-scm.com/book/en/v2)
* [A Visual Git Reference](https://git-scm.com/docs)
* [An interactive Git course](https://learngitbranching.js.org/)
* [Visualizing Git](https://git-school.github.io/visualizing-git/)

## Areas in a Git Repository

This diagram illustrates the different areas in a git repo and which
subcommands to use to manage changes between these buckets:

![Git areas](../img/gitbuckets.jpg)

## Configuration files

There are a number of configuration files that git offers and that let user
customize their git experience in great depth. As usual
great powers comes with great responsibility. :wink: Not all configuration
files and options are mentioned here, there
[are many more](https://git-scm.com/docs/git-config).

### First Time Git setup

This step is really important as you set some default behaviour and especially
you have to set your identity! This last step - configuring your identity - is
neglected very often. Please, don't. **Now go and read [first time git
setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)!**

Keep in mind that you just set your global identity. Almost every configuration
key is also changeable on repo level. This means while your global identity may
be "MrCool <cool@test.com>", you can still have another identity on a per repo
basis, i.e. when implementing stuff for work. You can set your identity within
the repo directory by issuing:

    git config user.name  "Max Mustermann"
    git config user.email max.mustermann@example.com

As you can see, the same command is run, but `--global` is left out. Now this
local setting can be found in the config file of the repo, `.git/config`. While
the global configuration file is found at `~/.gitconfig`.

Unsure what your identity is in the current repo? Just run `git config
user.name` or `git config user.email` respectively.

### Repo-local Configuration Files

#### `.gitignore` - Specifies intentionally untracked files to ignore

A gitignore file specifies intentionally untracked files that Git should ignore,
see [man gitignore](https://git-scm.com/docs/gitignore) or in the [git-book](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring).
This is valuable if you have some local temporary files, that should not get
committed except if forced. Other examples may include a vendor library that is
used that is versioned somewhere else and gets installed as a dependency.

#### `.gitattributes` - Defining attributes per path

A gitattributes file is a simple text file that gives attributes to pathnames,
i.e. end of line style, see [man gitattributes](https://git-scm.com/docs/gitattributes)
or in the [git-book](https://git-scm.com/book/en/v2/Customizing-Git-Git-Attributes).

## Articles

<!-- markdownlint-disable -->
### [The Thing About Git](https://tomayko.com/blog/2008/the-thing-about-git) <small>(15' read)</small>
<!-- markdownlint-restore -->

Often beginners find it oddly strange that there is an index/staging area in Git
and are not aware for what this thing can be used. Other VCS do not have this.
Nevertheless it's not an addition just to make Git more complicated and to
bother the developers. The "**Tangled Working Copy Problem**" illustrates why
this concept makes sense and how you should use it to your favor. There's one
important option tot `git add` that most beginners overlook (and tutorials
almost never teach you), e.g. `--patch` or `-p`

Try the following form of adding files to the index next you have to do that and
see what happens!  
`git add --patch somepathspec` or `git add -p somepathspec`
