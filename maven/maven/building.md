# Building the Project

Maven offers commands for most use cases. These work by giving a set of goals, marking how far into its lifecycle it will go:

```bash
mvn [goal]
```

Several goals can be combined. It is recommended using the 'clean' goal when generating artifacts:

```bash
mvn clean [goal]
```

This will delete all the generated content before starting.

To find more about these goals check the [Maven lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html).

## Setting up the Environment

If the POM is set up correctly all the dependencies and plugins will be handled automatically by Maven.

## Build

To generate the project artifacts \(JAR/WAR\):

```bash
mvn clean package
```

### Changing the Artifact Name

By default the generated artifact will include the version number, looking something like:

```text
project_id-version.jar
```

This can be changed by setting the final name build property:

```text
<build>
   <finalName>${project.artifactId}</finalName>
</build>
```

## Install

To install in the local repository:

```bash
mvn clean install
```

