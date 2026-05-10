# Work instructions

## Conda

The first step is optional but in our opinion worth the effort. Zensical is
software written in Python. As such it has dependencies and needs other
packages. Conda is one possible tool for dependency management for the languages
Python and R, see the [Wikipedia
page](https://en.wikipedia.org/wiki/Conda_(package_manager)) for a bigger
overview.

Knowing Conda helps to manage different Python environments that do not influence
each others. You can build a reusable environment that is at your fingertip in
many projects not just one.

!!! abstract "Task: Install Miniconda"

    - Install Miniconda
        - macOS: just install Miniconda with `brew`
        - Linux: use the installer, see [documentation](https://docs.conda.io/en/latest/miniconda.html)
    - Familiarize yourself with the `conda` command by using the getting started
      guide:
        - Create, activate, deactivate and destroy some test environments as outlined
          in the [Managing environments](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-environments)
        - Create environments with a specific version of Python, i.e. 3.14, see
          [Managing
        Python](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-python)
        - Install some packages with `conda` though we will use pip later when
          installing `zensical`, see [Managing
        packages](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-packages)
        - There is also a printable cheat sheet at the bottom of conda's getting
          started page.

## Zensical

Now we are ready to install the tool of choice - Zensical.

Zensical is a static site generator geared towards (technical) project
documentation with a modern responsive theme for the web and offers a lot more
features like a comprehensive search and a lot more of styling elements and
extensible with plugins. What you are currently reading is created using
Zensical, as is the [HPC user guide](https://hpc-unibe-ch.github.com/).

Documentation for the tools can be found on their websites at [Zensical documentation](https://zensical.org).

Having `conda` in place now lets us create a Conda environment for this tool.

!!! abstract "Task: Install Zensical in a Conda environment"

    - Create a Conda environment called "itjournal" and **activate it**
    - Install latest Python 3.14 (this also installs pip - the package manager)
    - Then install Zensical using pip.
    - Do you see the help message, when you run `zensical --help`?

Now that the `zensical` command is available, we can start our documentation -
versioned with Git and stored at GitHub.

!!!tip

    New to Git? Repeat Git Basics again? Go and watch the three videos right at
    the top of [Learning Git](../../gitandco/git/).

!!! abstract "Task: Create and initialize your journal"

    - Create a new directory, name as you like/see fit
    - Enter the directory and make it a git repository
    - Create a new personal GitHub repo over at [github.com](https://github.com)
    - Add the remote repo as the origin of your local git repo
    - Then create an initial Zensical project, use [get started guide](https://zensical.org/docs/get-started/)
    - Add and commit these files to the repository as first initial commit and
      starting point of your journey

!!! tip ""

    The documentation of [Zensical](https://zensical.org/docs/authoring/markdown/)
    itself is a valuable source for inspiration. Also this "demo/learning journal"
    may inspire you. Think especially about the structure of your documentation,
    where you want to publish the Tages- and Wochenberichte and probably some words
    about you.

Zensical has a built-in server to locally render and see, what the markdown you
are writing actually will look like when rendered to the static website, see
[Preview][4]. Make use of it and open
`https://localhost:8000` in you browser. It magically reloads upon changing
anything in your documentation, doesn't it?

!!! warning "Atomic Commits"

    Don't forget to do regular "atomic" commits, i.e. after changing a layout
    element or for each Wochenbericht.

## Publish at GitHub Pages

As soon as you work is done and you have something new to share with the world,
it's time to publish a new (or a first) version of your documentation. To
achieve this, `zensical` will build the static pages and these ca be published,
hence this is why the tool is a static code generator.

Managing the repository over at GitHub, we can publish the generated pages
using [GitHub Pages][5]. Although you already have a workflow in your project
directory, do it manually first.

!!! abstract "Task: Publish and verify"

    - View the video ["How to Use GitHub Pages in 2026?"](https://www.youtube.com/watch?v=5XhxR9Vs6zc)
    - Publish your journal using instruction at [Publishing your site](https://zensical.org/docs/publish-your-site/)
    - Where is your site published now? What is the URL to your rendered pages?

[4]: https://zensical.org/docs/usage/preview/
[5]: https://docs.github.com/en/pages
