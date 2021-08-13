# Git

## Learning Git

* [Visualizing Git](https://git-school.github.io/visualizing-git/)

TBD

* add some words about configuration and identities
* add PGP signing of commits
* add some notes about EOL and general style here?
* add gitignore and gitattributes examples
* introduce editorconfig
* other "in repo files"?

## .gitignore and .gitattributes

## Recipes

### `git push` rejected due to remote changes"

**Symptom**

I have committed something (to the main branch) and forgot to pull first. Now I can't push anymore as git
rejects the push with the following message:

!!! failure  "git push rejected"
    ![Screenshot](../img/git_push_reject.png)

**Discussion and Solution**

This usually means that somebody ellse already added a new commit and pushed to github and now your commit
conflicts with the other. What to do now? You would need to:

* Remove your commit(s) and keep the changes
* Run a `git pull --ff-only` to fetch the new commit from the other person
* Re-apply your changes again on top of the latest commit

!!! success "Solution"
    `git pull --rebase`

This command first fetches the latest commits and then rebases your commits on top of the latest commit, see `git help pull`. Now you may try to push your changes.

