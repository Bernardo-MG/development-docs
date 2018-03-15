# Project Setup

The setup.py file defines the project configuration. This is a script used to build the project, and also handle common usecases, such as testing or building the docs.

Additional configuration is contained in the setup.cfg file.

The MANIFEST.in file includes a list of files in the project.

A [Cookiecutter][cookiecutter] template exists and can be used to create new projects: the [Cookiecutter Python Library][cookiecutter_library].

## Dependencies

Dependencies are defined in the requirements.txt file, to be used with [pip][pip].

## Tests

Tests are handled with [tox][tox], and the tox.ini file defines profiles and scripts used to start the testing process.

## Documentation

[Sphinx][sphinx] is used to generate the project docs.

[cookiecutter]: https://github.com/audreyr/cookiecutter
[cookiecutter_library]: https://github.com/Bernardo-MG/cookiecutter-python-library
[pip]: https://pypi.python.org/pypi/pip
[sphinx]: http://www.sphinx-doc.org/
[tox]: https://tox.readthedocs.io