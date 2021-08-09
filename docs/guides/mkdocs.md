# MkDocs | Material for MkDocs

## Installation

There are many possible ways to install the tool and its dependencies, see
the [project's documentaiton](https://squidfunk.github.io/mkdocs-material/getting-started/).
The description below illustrates the conda environemnt way to go.

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
    # do more git stuff here or later
    # now initialize a mkdocs project
    # and add the files to the git index
    mkdocs new .
    git add .
    git ci -m "Initial empty mkdocs project"


The journey just started, best to continue the [Getting Started](https://squidfunk.github.io/mkdocs-material/creating-your-site/) guide on the material-mkdocs website.

## Further Reading

TBD
