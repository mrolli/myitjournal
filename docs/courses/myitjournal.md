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

Documention for the tools can be found on their websites at [https://www.mkdocs.org/](https://www.mkdocs.org/) and
[https://squidfunk.github.io/mkdocs-material/](https://squidfunk.github.io/mkdocs-material/).

Having conda in place now lets us create a conda environment for these tools.

!!! abstract "Task: Install Material for MkDocs"
    * Create a conda environment called "myitjournal" and ***activate it***
    * Install latest Python 3.9 (this also installs pip - the package manager)
    * Then install Material for MkDcos using pip

