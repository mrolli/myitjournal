# MkDocs | Material for MkDocs

## Installation

There are many possible ways to install the tool and its dependencies, see the
[getting started][1] guide of material-mkdocs. The description below illustrates
the conda environemnt way to go.

=== "Conda environment using pip"

    ```
    # Create conda environment and activate it
    conda create --name myenv
    conda activate myenv
    # Install latest Python 3.9.x
    conda install python=3.9
    # Install material-mkdocs and its dependencies, see output
    pip install mkdocs-material
    ```
    !!! info
        The above also install MkDocs and the python markdown extension (pymdown-extensions)

## Setup a project

Now its time to fire up a new projecct using `mkdocs:

    mkdir myproject
    cd myproject
    # It's probably wise to version it
    git init
    echo "site/" > .gitignore
    # Do more git stuff here or later
    #
    # Now initialize a mkdocs project
    # and add the files to the git index
    mkdocs new .
    git add .
    git ci -m "Initial empty mkdocs project"


The journey just started, best to continue the [getting started guide][1] of the
material-mkdocs website.

The [reference guide][2] of material-mkdocs is a superb place to get an overview
of possible style elements like admonitions, lists, formatting etc. and how to
achieve them. Also look into the [cheatsheet][3] with all stuff in aciton.

To publish the generated static pages, either deploy manually or setup a github action. This is
on page [Publish your site](https://squidfunk.github.io/mkdocs-material/publishing-your-site/).

## Further Reading

TBD

[1]: https://squidfunk.github.io/mkdocs-material/getting-started/
[2]: https://squidfunk.github.io/mkdocs-material/reference/abbreviations/
[3]: ../../mdcheat/
