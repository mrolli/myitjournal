# Zensical

[Zensical](https://zensical.org) is the successor of Material for MkDocs that
built on MkDocs. I migrated my stuff over to this drop-in replacement that is
actively developed.

## Installation

There are many possible ways to install the tool and its dependencies, see the
[getting started][1] guide of Zensical. The description below illustrates
two possible ways, using a virtual environment or a conda environment.

!!! tip

    Going the conda environment route, you create a conda environment that can
    be used for every Zensical project, while the virtual environment is
    project-local.

=== "Using virtual environment"

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate
    pip install zensical
    ```

=== "Conda environment using pip"

    ```bash
    # Create conda environment and activate it
    conda create --name myenv
    conda activate myenv
    # Install latest Python 3.14
    conda install python=3.14
    # Install zensical
    pip install zensical
    ```

## Setup a project

Now its time to fire up a new project using `zensical`:

    mkdir myproject
    cd myproject

    # Activate your chosen environment

    # It's probably wise to version the project
    git init
    echo "site/" > .gitignore

    # Now initialize a mkdocs project
    # and add the files to the git index
    zensical new .
    git add .
    git ci -m "Initial empty Zensical project"

The journey just started, best to continue the [getting started guide][1] of the
Zensical website.

The [usage][2], [setup][3] and [reference guide][4] of Zensical are superb
places to get an overview of possible style elements like admonitions, lists,
formatting etc. and how to achieve them. Also look into the [cheat sheet][5]
with all stuff in action.

To publish the generated static pages, either deploy manually or setup a GitHub
action. This is on page [Publish your site](https://zensical.org/docs/publish-your-site/).

## Further Reading

- [microsoft/markitdown](https://github.com/microsoft/markitdown)
- [Converting from/to markdown](http://www.tips.mostserio.us/cnvffmt/)

[1]: https://zensical.org/docs/get-started/
[2]: https://zensical.org/docs/usage/cli/
[3]: https://zensical.org/docs/setup/basics/
[4]: https://zensical.org/docs/authoring/markdown/
[5]: ../mdcheat.md
