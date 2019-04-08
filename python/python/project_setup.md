# Project Setup

The setup.py file defines the project configuration. This is a script used to build the project, and also handle common usecases, such as testing or building the docs.

Additional configuration is contained in the setup.cfg file.

The MANIFEST.in file includes a list of files in the project.

When creating new projects consider using a [template](https://github.com/bernardo-mg/development-docs/tree/607d3a34739325f64d3fc216771c0bc79458f781/python/templates/README.md).

## Dependencies

Dependencies are defined in the requirements.txt file, to be used with [pip](https://pypi.python.org/pypi/pip).

## Tests

Tests are handled with \[tox\]\[tox\], and the tox.ini file defines profiles and scripts used to start the testing process.

## Documentation

[Sphinx](http://www.sphinx-doc.org/) is used to generate the project docs.

\[tox\]: [https://tox.readthedocs.io](https://tox.readthedocs.io)

