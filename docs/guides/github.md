# GitHub

GitHub is a service to host repositories and provides a lot of features/utilities around this task. There are
many others but GitHub is the oldest and probably most used. GitHub provides extensive doucmentation and (video)
guides, so in order to honor the DRY principle, only little text is found here but instead a list of deep links to
chapters and other learning resources is provided here:

* [Training guides on GitHub and Git][gh-guides]
* [Video Guides on various topics](https://www.youtube.com/githubguides)
* [Create, cloning and archiving of repositories][gh-create]
* [Committing changes to your project][gh-commit]
* [Collaborating with pull requests / proposing changes to your work with PRs][gh-pullrequests]
* [Using the power of GitHub on the CLI][gh-cli]
* [GitHub Training Lab](https://lab.github.com/)
* [Visualizing Git](https://git-school.github.io/visualizing-git/)

## (Git) Workflows

When working in teams there are many possible workflows to work on a project all at the same minimizing the chnages
of conflicts. Hosting the repo at GitHub however should motivate you to incorporate the GitHub flow as it has proven
to be a very easy workflow that a whole lot of projects are using. Take a look into [guide on GitHub flow][gh-flow] with
a printable PDF.

TODO: Write on "issue -> PR -> merge"

**List of popular workflows**
* [GitHub flow][gh-flow]
* [A successful Git branching model AKA git-flow](https://medium.com/singlestone/a-git-workflow-using-rebase-1b1210de83e5)
* [Git workflow using rebase](https://medium.com/singlestone/a-git-workflow-using-rebase-1b1210de83e5)

Keep in mind to use a workflow that is as simple as possible. Do not overly complicate collaboraiton if it's no needed. The git-flow
workflow is very powerful but comes with a certain complexity and therefore too much of a hassle for most projects we do. For
these projects the [GitHub flow][gh-flow] is much more reasonable and by far easier to understand and live.

## GitHub on the CLI

There is a wonderful, official [tool][gh-cli] written in Go that let's you do all the GitHub related work on your CLI
wihtout the need to go to the browser. No need to switch app, enter URLs, click through to the destination page you need,
just to open a new PR. All can be done in your Bash. See it [in action][gh-cli].

## Community Health Files

TBD

[gh-create]: https://docs.github.com/en/github/creating-cloning-and-archiving-repositories
[gh-commit]: https://docs.github.com/en/github/committing-changes-to-your-project
[gh-collaborate]: https://docs.github.com/en/github/collaborating-with-pull-requests
[gh-pullrequests]: https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests
[gh-cli]: https://cli.github.com/
[gh-guides]: https://guides.github.com/
[gh-flow]: https://guides.github.com/introduction/flow/

