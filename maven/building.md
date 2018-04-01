# Building the Project

Maven offers commands for most use cases. These work by giving a set of goals, marking how far into its lifecycle it will go:

```
mvn [goal]
```

Several goals can be combined. It is recommended using the 'clean' goal when generating artifacts:

```
mvn clean [goal]
```

This will delete all the generated content before starting.

To find more about these goals check the [Maven lifecycle][maven_lifecycle].

## Setting up the environment

If the POM is set up correctly all the dependencies and plugins will be handled automatically by Maven.

## Build

To generate the project artifacts (JAR/WAR):

```
mvn clean package
```

## Install

To install in the local repository:

```
mvn clean install
```

[maven_lifecycle]: https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html
