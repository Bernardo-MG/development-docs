# Project Setup

Maven standard configuration is used. Avoid multi-module projects.

New projects can be created by using [Maven archetypes][maven_archetypes].

## Organization

When using Maven the project should follow the [Maven project layout][maven_layout].

## Dependencies

Dependencies are defined in the pom.xml file. This contains dependencies and plugins data, which Maven will handle.

## Tests

Testing is done with [JUnit][junit]. Maven will take care of running both unit and integration tests.

## Documentation

A Maven site is generated for each project.

[maven_archetypes]: ./archetypes.md
[maven_layout]: https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html

[junit]: https://junit.org/
