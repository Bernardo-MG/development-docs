# Documentation

Documentation should aim to cover two usecases:
* Developers, who must be able to understand the implementation
* Users, who must be able to understand the API

## Documentation components

There is not a single way to document a project, but the following should be part of any project:
* Readme
* License info
* Generated documentation site
* Issues tracking

The readme and license info are included in the project folder, at its root so they are among the first files to be noticed, but the other two should be accessible through a remote server.

There are several services and applications for the issues tracker, and there are some for generated documentation, such as [RTD][rtd] or [GitBook][gitbook], but in some cases the documentation will require a static content server, for example when generating a [Maven site][maven_site].

### Readme

The readme should give a quick introduction to the project. It is not a manual by itself, but a quick start guide. After reading it anybody should be able to know what the project is about, who is working on it and where to start if he wants to use or modify it.

Currently the readmes are being divided into the following sections:

* Introduction
* Features
* Documentation
* Usage, including prerequisites and installation
* How to collaborate
* License

## Diagrams

Visual diagrams will follow the UML specifications.

The tool used for creating them us [UMLet][umlet], a free Eclipse-based UML editor. It is very simple, and this way allows a lot of flexibility, but is not capable of auto generating code.

[gitbook]: https://www.gitbook.com
[maven_site]: https://maven.apache.org/plugins/maven-site-plugin/
[rtd]: https://readthedocs.org/
[umlet]: http://www.umlet.com/