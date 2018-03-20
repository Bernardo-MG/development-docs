# Documentation

Documentation should aim to two audiences:

* Developers, who must be able to understand the implementation
* Users, who must be able to understand the API

## Documentation components

There is not a single way to document a project, but the following points should be included in the project:

* Readme
* License info
* Generated documentation site
* Issues tracking

The readme and license info are included in the project root folder, so they are among the first files to be noticed.

There are several services and applications for the issues tracker. The one offered by Github is recommended, just because it comes with the repository.

For generated documentation services such as [RTD][rtd] or [GitBook][gitbook] can be used. But in some cases the documentation will require a static content server, for example when generating a [Maven site][maven_site].

### Readme

The readme should give a quick introduction to the project. It is not a manual by itself, but a quick-start guide. After reading it anybody should know what the project is about, who is working on it and where to start if he wants to use or modify it.

Currently the readmes are being divided into the following sections:

* Introduction
* Features
* Documentation
* Usage, including prerequisites and installation
* How to collaborate
* License

## Diagrams

Visual diagrams are helpful for documentation. These should follow the UML specifications.

The tool used for creating them us [UMLet][umlet], a free Eclipse-based UML editor. It is very simple, and this allows a lot of flexibility, but is not capable of any advanced feature such as generating code.

## References

* [Write the Docs][write_the_docs]

[gitbook]: https://www.gitbook.com
[maven_site]: https://maven.apache.org/plugins/maven-site-plugin/
[rtd]: https://readthedocs.org/
[umlet]: http://www.umlet.com/
[write_the_docs]: http://www.writethedocs.org/guide/