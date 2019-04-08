# Project Setup

Maven standard configuration is used. Avoid multi-module projects.

New projects can be created by using [Maven archetypes](https://github.com/bernardo-mg/development-docs/tree/607d3a34739325f64d3fc216771c0bc79458f781/maven/configuration/archetypes.md).

## Organization

When using Maven the project should follow the [Maven project layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html).

## Dependencies

Dependencies are defined in the pom.xml file. This contains dependencies and plugins data, which Maven will handle.

## Tests

Testing is done with [JUnit](https://junit.org/). Maven will take care of running both unit and integration tests.

## Documentation

A Maven site is generated for each project.

