# Building the Project

All the Python projects contain a setup.py file, used to build the project.

It can be used through commands like:

```text
python setup.py [command]
```

All the available commands can be listed with:

```text
python setup.py --help-commands
```

## Setting up the environment

Before building all the requirements should be installed:

```text
pip install --upgrade -r requirements.txt
```

## Build

To build everything needed to install the project:

```text
python setup.py build
```

## Distribution

To generate a distributable copy of the project:

```text
python setup.py sdist
```

## Install

To install in the local repository:

```text
python setup.py install
```

