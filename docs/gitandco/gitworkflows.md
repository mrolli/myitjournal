# Git Workflows

While Git is the tool of choice to version any kind of text files, it is only
doing exactly that. It makes now assumption about how people work together.
Coming up with a decent workflow is up to the user working with the tool Git.

## [A successful Git branching model][gitflow] <small>(20' read)</small>

This article is the original article from 2010 that introduced/presented the
Git-flow workflow for managing the code for software projects. It was the first
workflow that was widely adopted and got "famous". The articles demonstrates a
lot of brain work done about handling different situations and how
to solve issues. **But also read the author's reflection at the top! While this
is a proven Git branching strategy it is quite complex and for many situations
and projects a complete overkill.**  
Keep in mind to use a workflow that is as simple as possible. Do not overly
complicate collaboration if it's not needed. The git-flow workflow is very
powerful but comes with a certain complexity and therefore too much of a hassle
for most projects we do. For these projects the [GitHub flow][gh-flow] is much
more reasonable and by far easier to understand and live.

There is a good [comparison of git branching strategies][gbstrats]
over at flaghsip.io. You should at least know the principles, pros/cons and
differences between these four strategies.

Make yourself familiar with other Git branching strategies like the ones in the
following list and then **choose the simplest that is still satisfying your real
needs (not the nice to haves)**. Also use something that others in your team are
already familiar and successful with!

## List of popular Git workflows

- GitHub flow [Discussion][gh-flow] and [Documentation][githubflow]
- [GitLab Flow][gitlabflow]
- [git-flow][gitflow]
- [Git workflow using rebase](https://medium.com/singlestone/a-git-workflow-using-rebase-1b1210de83e5)

When working in teams there are many possible workflows to work on a project all
at the same minimizing the changes of conflicts. Hosting the repo at GitHub
however should motivate you to incorporate the GitHub flow as it has proven to
be a very easy workflow that a whole lot of projects are using. Take a look into
[guide on GitHub flow][gh-flow].

[gh-flow]: https://guides.github.com/introduction/flow/
[githubflow]: https://githubflow.github.io/
[gitflow]: https://nvie.com/posts/a-successful-git-branching-model/
[gitlabflow]: https://docs.gitlab.com/ee/topics/gitlab_flow.html
[gbstrats]: https://www.flagship.io/git-branching-strategies/
