# Building the project

All the Python projects contain a setup.py file, used to build the project.

It can be used through commands like:

```
python setup.py [command]
```

All the available commands can be listed with:

```
python setup.py --help-commands
```

## Setting up the environment

Before building all the requirements should be installed:

```
pip install --upgrade -r requirements.txt
```

## Build

To build everything needed to install the project:

```
python setup.py build
```

## Distribution

To generate a distributable copy of the project:

```
python setup.py sdist
```

## Install

To install in the local repository:

```
python setup.py install
```
