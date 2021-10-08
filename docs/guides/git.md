# Git

## Learning Git

* [Pro Git Book](https://git-scm.com/book/en/v2)
* [Visualizing Git](https://git-school.github.io/visualizing-git/)

## Configuration files

There are a number of configuration files that git offers and that let user customize their git experience in great depth. As usual
great powers comes with great responsibility. :wink: Not all configuration files and options are mentioned here, there
[are many more](https://git-scm.com/docs/git-config).

### Repo-local

#### *gitignore* - Specifies intentionally untracked files to ignore

A gitignore file specifies intentionally untracked files that Git should ignore, see [man gitignore](https://git-scm.com/docs/gitignore) or in the [git-book](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring).

#### *gitattributes* - Defining attributes per path

A gitattributes file is a simple text file that gives attributes to pathnames, i.e. end of line style, see
[man gitattributes](https://git-scm.com/docs/gitattributes) or in the [git-book](https://git-scm.com/book/en/v2/Customizing-Git-Git-Attributes).

## Articles

#### **[The Thing About Git](https://tomayko.com/blog/2008/the-thing-about-git)**

Often beginners find it oddly strange that there is an index/staging area in Git and are not aware
for what this thing can be used. Other VCS do not have this. Nevertheless it's not an addition just
to make Git more complicated and to bother the developers. The "**Tangled Working Copy Problem**" illustrates
why this concept makes sense and how you should use it to your favor. There's one important option tot `git add`
that most beginners overlook (and tutorials almost never teach you), e.g. `--patch` or `-p`

Try the following form of adding files to the index next you have to do that and see what happens!
`git add --patch somepathspec` or `git add -p somepathspec`

## Recipes

### `git push` rejected due to remote changes

**Symptom**

I have committed something (to the main branch) and forgot to pull first. Now I can't push anymore as git
rejects the push with the following message:

!!! failure  "git push rejected"
    ![Screenshot](../img/git_push_reject.png)

**Discussion and Solution**

This usually means that somebody else already added a new commit and pushed to GitHub and now your commit
conflicts with the other. What to do now? You would need to:

* Remove your commit(s) and keep the changes
* Run a `git pull --ff-only` to fetch the new commit from the other person
* Re-apply your changes again on top of the latest commit

!!! success "Solution"
    `git pull --rebase`

This command first fetches the latest commits and then rebases your commits on top of the latest commit, see `git help pull`. Now you may try to push your changes.

### Damn, I committed a secret!

**Symptom**

You just committed a configuration file with a password in it? You entered a real password into a file instead of a dummy password like
`123456` and committed it? You added disclosed something else by committing it to the repo? Fear not and read ahead!

**Discussion and Solution**

There's good [cheat sheet from GitGuardian](../pdf/RewritingYourGitHistory-Cheatsheet.pdf) that features a flow chart on how
to proceed and save the situation depending on the stage at which you realised that something wrong happened.
