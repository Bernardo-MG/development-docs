# Project Setup

Maven standard configuration is used. Avoid multi-module projects.

New projects can be created by using [Maven archetypes][maven_archetypes].

## Dependencies

Dependencies are defined in the pom.xml file. This contains dependencies and plugins data, which Maven will handle.

## Tests

Testing is done with [JUnit][junit]. Maven will take care of running both unit and integration tests.

## Documentation

A Maven site is generated for each project.

[maven_archetypes]: ./templates

[junit]: https://junit.org/
