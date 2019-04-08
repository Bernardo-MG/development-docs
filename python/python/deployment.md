# Deployment

## Deployment

Libraries are to be deployed to [PyPi](https://pypi.python.org/pypi) with the help of [pip](https://pypi.python.org/pypi/pip).

More detailed information can be found at the [distributing packages tutorial](https://packaging.python.org/tutorials/distributing-packages/).

## Deploying a distribution

First of all build the project by using one of the following commands.

To build the source distribution:

```text
python setup.py sdist
```

To build the [Wheel](https://github.com/pypa/wheel) distribution \(requires installing the wheel package\):

```text
python setup.py bdist_wheel
```

If possible build both, then deploy them.

[twine](https://github.com/pypa/twine) can be used to deploy securely:

```text
twine upload dist/*
```

### Test deployment

There is a [test environment for PyPi](https://testpypi.python.org/pypi).

To deploy:

```text
$ python setup.py sdist upload -r pypitest
```

### Deployment configuration

Deploying to Pypi requires authentication. This is handled with a '.pypirc' file, located in the user folder.

It should contain something similar to:

```text
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

