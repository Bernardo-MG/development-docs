# Deployment

Libraries are to be deployed to [PyPi][pypi] with the help of [pip][pip].

More detailed information can be found at the [distributing packages tutorial][distributing_packages].

# Deploying a distribution

First of all build the project by using one of the following commands.

To build the source distribution:

```
python setup.py sdist
```

To build the [Wheel][wheel] distribution (requires installing the wheel package):

```
python setup.py bdist_wheel
```

If possible build both, then deploy them.

[twine][twine] can be used to deploy securely:

```
twine upload dist/*
```

## Test deployment

There is a [test environment for PyPi][pypitest].

To deploy:

```
$ python setup.py sdist upload -r pypitest
```

## Deployment configuration

Deploying to Pypi requires authentication. This is handled with a '.pypirc' file, located in the user folder.

It should contain something similar to:

```
[distutils]
index-servers =
    pypi
    pypitest

[pypi]
username: username_pypi
password: password_pypi

[pypitest]
repository: https://testpypi.python.org/pypi
username: username_pypitest
password: password_pypitest
```

This example defines authentication data for PyPi and for the PyPi test server.

[pip]: https://pypi.python.org/pypi/pip
[pypi]: https://pypi.python.org/pypi
[pypitest]: https://testpypi.python.org/pypi

[twine]: https://github.com/pypa/twine
[wheel]: https://github.com/pypa/wheel

[distributing_packages]: https://packaging.python.org/tutorials/distributing-packages/
