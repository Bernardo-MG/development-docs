# PyPi

[PyPi][pypi] is a package repository for Python. Along with [pip][pip] it can be used for dependency management.

## Dependency management

This is already covered in the PyPi documentation and many tutorials.

It will be enough saying that dependencies are defined in the requirements.txt file inside the Python projects.

## Useful commands

### Install requirements for the project

This should be run from the project root, where a requirements file should exist.

```
$ pip install --upgrade -r requirements.txt
```

### Install a dependency into the local repository

```
$ pip install [dependency-name]
```

[pip]: https://pypi.python.org/pypi/pip
[pypi]: https://pypi.python.org/pypi
