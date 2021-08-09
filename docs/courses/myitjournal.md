# My IT Journal

This is our first project. We want to generate a documentaiton where you can write
down your daily and weekly reports that you must write. Previously you have done this
in the Confluence Wiki of Informatikdienste. Wouldn't it be nicer to have it somewhat
more accessible and more modern? You can even buld a showcase of your skills with it!

Now let us first define the requirements and the goals of our solution:

* The documentation must be verioned, therefore we want to manage it in a Git repository.
* Being in a Git repository and published on github.com allows others to participate.
* As a learner I don't want to wr

## Conda

The first step is optional but in our opinion worth the effort. MkDocs is software written
in Python. As such it has dependencies and need other packages. Conda is the defacto standard
for dependency management for the languages Pyhton and R, see the
[Wikipedia page](https://en.wikipedia.org/wiki/Conda_(package_manager)) for a bigger overview.

Knowing conda helps to manage different Python environments that do not influence each others.

!!! abstract "Task: Install Miniconda"
    * Install Miniconda
        * macOS: just install miniconda with `brew`
        * Linux: use the installer, see [documentation](https://docs.conda.io/en/latest/miniconda.html)
    * Familiarize yourself with conda by using the getting started guide:
        * Create, activate, deactivate and destroy some test environments as outlined
          in the [Managing environments](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-environments)
        * Create environments with a specific version of Pythyon, i.e. 3.9.x, see [Managing Python](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-python)
        * Install some packages with conda though we will use pip later when installing `mkdocs`, see [Managing packages](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-packages)
        * There is also a printable cheat sheet at the bottom of this very page.
    

## MkDocs and Material for MkDocs

Now we are ready to install the tool of choice - MkDocs. We will not only install MkDocs itself
but the package "Material for MkDocs".

Material for MkDocs is a theme for MkDocs, which itself is a static site generator geared towards
(technical) project documentation. This is the tool used to create our [HPC used guide](https://hpc-unibe-ch.github.com/).

Documentation for the tools can be found on their websites at [https://www.mkdocs.org/](https://www.mkdocs.org/) and
[https://squidfunk.github.io/mkdocs-material/](https://squidfunk.github.io/mkdocs-material/).

Having conda in place now lets us create a conda environment for these tools.

!!! abstract "Task: Install Material for MkDocs"
    * Create a conda environment called "itjournal" and ***activate it***
    * Install latest Python 3.9 (this also installs pip - the package manager)
    * Then install Material for MkDcos using pip
    * Do you see the help message, when you run `mkdocs --help`?

Now that the mkdocs tool and the respective Material theme is installed, we can start our documentation.

!!! abstract "Task: Create and initialize your journal"
    * Create a new directory, name as you like/see fit
    * Enter the directory and make it a git repository
    * Create a new github repo over at [github.com](https://github.com)
    * Add the remote repo as the origin of your local git repo
    * Then create an initial mkdocs project, see getting started guide of mkdocs-material
    * Add and commit these files as the starting point of your journey

!!! tip ""
    The documentation of [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) itself
    is a valuable source for inspiration. Also this "demo/learning journal" may inspire you. Think
    espcially about the structure of your docomentation, where you want to publish the Tages- and
    Wochenberichte and probably some words about you.

MkDocs features a built in server to locally render and see, what the markdown you are writing
actually will look like, see chapter "Preview as you write". Make use of it and open
`https://localhost:8000` in you browser. It magically reloads upon changing anyhting in your
documentation, doesn't it?

!!! warning ""
    Don't forget to do regular commits, i.e. after changing a layout element or for each Tages- or
    Wochenbericht.

As soon as you work is done and you have something new to share with the world, it's time to 
publish a new (or a first) version of your documentation. To achieve this, `mkdocs` will build
the static pages and to publish the result. When managing the repo on github.com and publishing
as gihtub pages at github.io, things are very easy to acomplish. github.com will automatically 
see the generate `gh-pages` branch that mkdocs generates. Things "automagically" just work as
expected. Nevertheless...

!!! acstract "Task: Publish and verify"
    * View the "What is GitHub Pages" Video at [https://www.youtube.com/watch?v=2MsN8gpT6jY](https://www.youtube.com/watch?v=2MsN8gpT6jY)
    * Use mkdocs to publish as github pages, see "with MkDocs" on [Publishing your site](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#with-github-actions)

Later we will improve the project to automatically build the static pages on every push to the main
branch, but for now, we do it manually to get used to it.
