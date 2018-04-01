# Maven

[Maven][maven] is a project management tool for Java. In some aspects it may be too big, offering much more than what most people will need, and suffering integration problems with itself from time to time. Still, used with care it is really useful.

Its most useful aspects are:
- Dependency management
- Project management (building, running tests, deploying...)
- Generating documentation site

## Lifecycle

To understand Maven one first needs to understand the [Maven lifecycle][maven_lifecycle]

## Dependency management

This is already covered in the Maven documentation and many tutorials.

Some rules:

* Never use snapshots in releases
* Ensure version convergence

### Version management

Handling dependencies includes controlling the versions of those dependencies. Maven allows doing so without actually including the versions into the project.

This is handled with the [dependency management][maven_dependency_management] and [plugin management][maven_plugin_management] options.

This way if the dependencies are added into any kind of children POM the version is already set by default. Which is very useful when creating base POMs or working with multi-module projects.

### Checking for updates

To check if there are newer versions for the dependencies use the following command:

```
mvn versions:display-dependency-updates versions:display-plugin-updates
```

## Settings file

Sensitive information, such as authentication data, should be moved to a [Maven settings file][maven_settings], located in a secure path.

Then it can be loaded by Maven with any command:

```
mvn deploy --settings ~/settings.xml
```

[maven]: https://maven.apache.org/
[maven_lifecycle]: https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html
[maven_dependency_management]: https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html#Dependency_Management
[maven_plugin_management]: https://maven.apache.org/pom.html#Plugin_Management
[maven_settings]: https://maven.apache.org/settings.html
