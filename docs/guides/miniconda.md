# Miniconda

The fastest way to obtain conda is to install [Miniconda](https://docs.conda.io/en/latest/miniconda.html),
a mini version of Anaconda that includes only conda and its dependencies. If you
prefer to have conda plus over 7,500 open-source packages, install Anaconda.

## Installation

=== "macOS (Homebrew)"
    On macOS it's easiest to use Homebrew for the task:
        ```bash
        brew install miniconda

        ```

=== "macOS (Installer Script)"
    See [project documentaiton][1] for the installer script.

=== "Linux (Installer Script"
    See [project documentaiton][1]

[1]: https://docs.conda.io/en/latest/miniconda.html

## Managing Environments

### Create an environment

The following two tabs illustrate how to create an environment and install packages
manually with several commands while the other shows how to build an environment
based on specifications found in a YAML file.

=== "manually"

    ```
    # Create conda environment and activate it
    conda create --name myenv
    conda activate myenv
    # Install latest Python 3.9.x
    conda install python=3.9
    # Install some package and its depepdencies
    pip install mkdocs-material
    ```

=== "from file"

    ```
    # Create a yaml file specifiying the details of the env to create
    cat <<EOD >~/environment.yml
    name: myenv
    dependencies:
      - python=3.9
      - pip:
          - mkdocs-material
    EOD
    # the -f option can even be ommitted if the environment file is named
    # environment.yaml and is found within current workig directory
    conda create [-f environment.yml]
    ```

!!! tip "Add environment.yml to git repo"
    When having a python environemnt for project, it's good practice to have the
    specification in a file `environment.yml` toplevel in the git repo of the project.
    Like this, you document what needs to be install and you (and your contributors)
    can fire up the evironment by just cloning the repo and running `conda create`
    within the toplevel directory. Done.

### Managing environments

Further commands regarding the management of environments outlined in the [documentation]
in good details. Have a look there!

[documentation]: https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-environments
