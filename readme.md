# Wandrell's Development Docs

This is a personal programming guide, to help myself when developing a software project. It explains the methodologies I use and prefer, and how to use them.

## Building the docs

The docs source is composed of reStructuredText files, prepared for [Sphinx][sphinx]. This means that they can easily be built into many different documents. Even more easily if you take into account the included Makefile (and make bat for Windows).

For example, to build a static html site just use the following command:

```
make html
```

## Collaborate

Any kind of help with the project will be well received. Any recommendation or tip can be added to the issue management and will be taken into account.

Of course everybody is free to fork and adapt the project for their own use.

### Issues management

Issues are managed at the GitHub [project issues tracker][issues], where any Github user may report bugs or ask for new features.

### Getting the code


If you wish to fork or modify the code, visit the [GitHub project page][scm], where the latest versions are always kept. Check the 'master' branch for the latest release, and the 'develop' for the current, and stable, development version.

## License

The project has been released under the [MIT License][license].

[issues]: https://github.com/bernardo-mg/development-docs/issues
[license]: http://www.opensource.org/licenses/mit-license.php
[scm]: https://github.com/bernardo-mg/development-docs

[sphinx]: http://www.sphinx-doc.org/
