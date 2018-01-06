# Deployment

Libraries are to be deployed to [PyPi][pypi] with the help of [pip][pip].

The following commands handle this:

```
$ python setup.py sdist
$ twine upload dist/*
```

The first command will create the source distribution, and then [twine][twine] is used for the deployment.

If this is a new project then it may require being registered prior to deployment:

```
$ python setup.py register -r pypi
```

## Test deployment

There is a [test environment for PyPi][pypitest].

A project can be registered into it:

```
$ python setup.py register -r pypitest
```

And then deployed:

```
$ python setup.py sdist upload -r pypitest
```

[pip]: https://pypi.python.org/pypi/pip
[pypi]: https://pypi.python.org/pypi
[pypitest]: https://testpypi.python.org/pypi
[twine]: https://github.com/pypa/twine
