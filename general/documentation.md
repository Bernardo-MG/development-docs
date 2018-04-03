# Documentation

Documentation has two audiences:

* Users, who must be able to understand the API
* Developers, who must be able to understand the implementation

## Documentation components

There is not a single way to document a project, but the following should be included in the project:

* Readme
* License info
* Generated documentation site
* Issues tracking

### Readme

The readme should give a quick introduction to the project and be included in the project root to be noticed fast.

It is not a manual by itself, but a quick-start guide. After reading it anybody should know what the project is about, who is working on it and where to start if he wants to use or modify it.

Currently the readmes are being divided into the following sections:

* Introduction
* Features
* Documentation
* Usage, including prerequisites and installation
* How to collaborate
* License

### License

The license file should use a standard license and be included in the project root to be noticed fast. This tells developers what they can do with the application.

Check a licenses guide:

- [Choose a License][choose_license]

Recommended licenses:

- MIT license for simple projects or examples, meant for a wide use
- Apache 2 license for more complex projects, meant for a specific range of users

### Generated documentation site

There are services for generates documentation:

- [RTD][rtd]
- [GitBook][gitbook]

And tools for generating documentation:

- [Sphinx][sphinx]
- [Maven site][maven_site]
- [Jekyll][jekyll]

More details will be given in other chapters.

### Issues Tracker

There are several services and applications for the issues tracker.

If using Github, it offers one for every repository.

Some alternatives which require a server:

- [Redmine][redmine]
- [Jira][jira]

## Diagrams

Visual diagrams are helpful for documentation. These should follow the UML specifications.

Tools for creating diagrams:

- [UMLet][umlet], free and simple Eclipse-based UML editor
- [Enterprise Architect][enterprise_architect]

## Additional information

* [Write the Docs][write_the_docs]

[choose_license]: https://choosealicense.com/
[enterprise_architect]: sparxsystems.com/products/ea/
[gitbook]: https://www.gitbook.com
[jekyll]: https://jekyllrb.com/
[jira]: https://www.atlassian.com/software/jira
[maven_site]: https://maven.apache.org/plugins/maven-site-plugin/
[redmine]: https://www.redmine.org/
[rtd]: https://readthedocs.org/
[sphinx]: http://www.sphinx-doc.org
[umlet]: http://www.umlet.com/
[write_the_docs]: http://www.writethedocs.org/guide/
