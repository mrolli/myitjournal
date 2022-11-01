# My IT Journal

This is our first project. We want to create a documentation where you can write
down your daily and weekly reports that you are obliged to write. Previously you
have done this in the Confluence Wiki of Informatikdienste. Wouldn't it be nicer
to have it somewhat more accessible and more modern? You can even build a
showcase of your skills with it!

Now let us first define the requirements and the goals of our solution:

* The documentation must be versioned, therefore we want to manage it in a Git repository.
* Being in a Git repository and published over at https://github.com allows others to participate.
* As a learner I don't want to write this webpage using HTML, Javascript and CSS but use a framework
  that creates static code. The framework must allow me to write markdown.

## Conda

The first step is optional but in our opinion worth the effort. MkDocs is
software written in Python. As such it has dependencies and needs other
packages. Conda is one possible tool for dependency management for the languages
Python and R, see the [Wikipedia
page](https://en.wikipedia.org/wiki/Conda_(package_manager)) for a bigger
overview.

Knowing Conda helps to manage different Python environments that do not influence each others.

!!! abstract "Task: Install Miniconda"
    * Install Miniconda
        * macOS: just install Miniconda with `brew`
        * Linux: use the installer, see [documentation](https://docs.conda.io/en/latest/miniconda.html)
    * Familiarize yourself with the `conda` command by using the getting started guide:
        * Create, activate, deactivate and destroy some test environments as outlined
          in the [Managing environments](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-environments)
        * Create environments with a specific version of Python, i.e. 3.9.x, see [Managing
        Python](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-python)
        * Install some packages with `conda` though we will use pip later when installing `mkdocs`, see [Managing
        packages](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-packages)
        * There is also a printable cheat sheet at the bottom of conda's getting started page.


## MkDocs and Material for MkDocs

Now we are ready to install the tool of choice - MkDocs. We will not only
install MkDocs itself but also the package "Material for MkDocs".

MkDocs itself is a static site generator geared towards (technical) project
documentation. Material for MkDocs is an additional package providing a modern
responsive them for the web and a lot more features like a comprehensive search
and a lot more of styling elements that what MkDocs itself provides. Those two
packages are used to create our [HPC used
guide](https://hpc-unibe-ch.github.com/).

Documentation for the tools can be found on their websites at
[https://www.mkdocs.org/](https://www.mkdocs.org/) and
[https://squidfunk.github.io/mkdocs-material/](https://squidfunk.github.io/mkdocs-material/).
The latter is very good and will help in every aspect. Stick primarily to this
source!

Having `conda` in place now lets us create a Conda environment for these tools.

!!! abstract "Task: Install Material for MkDocs"
    * Create a Conda environment called "itjournal" and **activate it**
    * Install latest Python 3.x (this also installs pip - the package manager)
    * Then install Material for MkDocs using pip. Notice that MkDocs itself gets
      automatically installed as it is a dependency of Material for MkDocs.
    * Do you see the help message, when you run `mkdocs --help`?

Now that the `mkdocs` command is available and the respective Material theme is
installed, we can start our documentation.

!!! abstract "Task: Create and initialize your journal"
    * Create a new directory, name as you like/see fit
    * Enter the directory and make it a git repository
    * Create a new GitHub repo over at [github.com](https://github.com)
    * Add the remote repo as the origin of your local git repo
    * Then create an initial MkDocs project, see getting started guide of
      mkdocs-material
    * Add and commit these files to the repository as first initial commit and
      starting point of your journey

!!! tip ""
    The documentation of [Material for
    MkDocs](https://squidfunk.github.io/mkdocs-material/) itself is a valuable
    source for inspiration. Also this "demo/learning journal" may inspire you. Think
    especially about the structure of your documentation, where you want to publish
    the Tages- and Wochenberichte and probably some words about you.

MkDocs has a built-in server to locally render and see, what the markdown you
are writing actually will look like when rendered to the static website, see
chapter [Preview as you write][4]. Make use of it and open
`https://localhost:8000` in you browser. It magically reloads upon changing
anything in your documentation, doesn't it?

!!! warning ""
    Don't forget to do regular "atomic" commits, i.e. after changing a layout
    element or for each Tages- or Wochenbericht.

As soon as you work is done and you have something new to share with the world,
it's time to publish a new (or a first) version of your documentation. To
achieve this, `mkdocs` will build the static pages and publishes the result.
Managing the repository over at github.com and publishing as GitHub pages at
github.io, things are very easy to accomplish. github.com will automatically
recognize the created `gh-pages` branch that `mkdocs` generates. Things
"automagically" just work as expected. Nevertheless...

!!! abstract "Task: Publish and verify"
    * View the "What is GitHub Pages" Video at [https://www.youtube.com/watch?v=2MsN8gpT6jY][5]
    * Use `mkdocs` to publish as GitHub pages, see section "with MkDocs" at the page [Publishing your site][6]
    * Where is your site published now? What is the URL to your rendered pages?

Later we will improve the project to automatically build the static pages on
every push to the main branch, but for now, we do it manually to get used to it.

[4]: https://squidfunk.github.io/mkdocs-material/creating-your-site/#previewing-as-you-write
[5]: https://www.youtube.com/watch?v=2MsN8gpT6jY
[6]: https://squidfunk.github.io/mkdocs-material/publishing-your-site/#with-github-actions
