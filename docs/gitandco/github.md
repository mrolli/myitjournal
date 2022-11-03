# GitHub

GitHub is a service to host repositories and provides a lot of
features/utilities around this task. There are many others but GitHub is the
oldest and probably most used. GitHub provides extensive documentation and
(video) guides, so in order to honor the DRY principle, only little text is
found here but instead a list of deep links to chapters and other learning
resources is provided here:

- [Training guides on GitHub and Git][gh-guides]
- [Video Guides on various topics](https://www.youtube.com/githubguides)
- [Create, cloning and archiving of repositories][gh-create]
- [Committing changes to your project][gh-commit]
- [Collaborating with pull requests / proposing changes to your work with PRs][gh-collaborate]
- [Proposing changes to your work with pull requests][gh-pullrequests]
- [Using the power of GitHub on the CLI][gh-cli]
- [GitHub Training Lab](https://lab.github.com/)
- [Visualizing Git](https://git-school.github.io/visualizing-git/)

## (Git) Workflows

When working in teams there are many possible workflows to work on a project all
at the same minimizing the changes of conflicts. Hosting the repo at GitHub
however should motivate you to incorporate the GitHub flow as it has proven to
be a very easy workflow that a whole lot of projects are using. Take a look into
[guide on GitHub flow][gh-flow].

### Example Workflow The philosophy of mine is that every change should be

documented from the beginning to the end when it's implemented. A change could
be a bug and its fix or a new feature that is required and gets implemented. The
order of action then is:

1. Open a ticket and describe the bug/feature in several dimensions to make it
   possible to understand the need to change something. Key questions are:
    - What is broken?
    - How does the error present itself?
    - What are error messages that occur?
    - What feature is missing?
    - Which are the requirements that make the changes necessary?
1. Checkout a new branch that addresses this issue and implement the changes on
   this branch? Name the branch accordingly,
    i.e. `issue31`, `featureXY`, ...
1. Make changes and commits to this feature branch
1. (optional): Cleanup the branch by rewording, squashing, rearranging commits
   using  `git rebase --interactive`
1. Push your changes to origin
1. Prepare a pull request and optionally ask someone else to review the changes
1. Merge the feature branch back into the `main` branch
1. Delete the feature branch locally and remote
1. Get yourself a :beer: or move to the next ticket

**List of popular workflows**

- [GitHub flow][gh-flow]
- [A successful Git branching model AKA git-flow](https://medium.com/singlestone/a-git-workflow-using-rebase-1b1210de83e5)
- [Git workflow using rebase](https://medium.com/singlestone/a-git-workflow-using-rebase-1b1210de83e5)

Keep in mind to use a workflow that is as simple as possible. Do not overly
complicate collaboration if it's no needed. The git-flow workflow is very
powerful but comes with a certain complexity and therefore too much of a hassle
for most projects we do. For these projects the [GitHub flow][gh-flow] is much
more reasonable and by far easier to understand and live.

## GitHub Actions

Except for the following deep links into the official documentation, no other
information is available here as of yet.

- [Using workflows](https://docs.github.com/en/actions/using-workflows#creating-a-workflow-file)
- [Workflow Syntax for GitHub Actions](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Supported platforms for action runners](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idruns-on)

## GitHub on the CLI

There is a wonderful, official [tool][gh-cli] written in Go that let's you do
all the GitHub related work on your CLI without the need to go to the browser.
No need to switch app, enter URLs, click through to the destination page you
need, just to open a new PR. All can be done in your Bash. See it [in
action][gh-cli].

## Community Health Files

TBD

[gh-create]: https://docs.github.com/en/github/creating-cloning-and-archiving-repositories
[gh-commit]: https://docs.github.com/en/github/committing-changes-to-your-project
[gh-collaborate]: https://docs.github.com/en/github/collaborating-with-pull-requests
[gh-pullrequests]: https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests
[gh-cli]: https://cli.github.com/
[gh-guides]: https://guides.github.com/
[gh-flow]: https://guides.github.com/introduction/flow/
