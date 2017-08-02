# Maven

[Maven][maven] is a project management tool for Java. In some aspects it may be too big, offering much more than what most people will need, and suffering integration problems with itself from time to time. Still, used with care it is really useful.

The main aspects used in the projects are:
- Dependency management
- Project management (building, running tests, deploying...)
- Generating documentation site

## Dependency management

This is already covered in the Maven documentation and many tutorials.

## Version management

It should be noted that Maven allows not only setting a project's dependencies, but also the versions of those dependencies without adding them. This way if the dependencies are added into any kind of children POM the version is already set by default.

This is handled with the [dependency management][maven_dependency_management] and [plugin management][maven_plugin_management] options.

## Project management

### Base POM

Common configuration for multiple projects should be kept inside a base POM. The main one is in the project plainly name [base POM][base_pom], a generic POM to be used in most kinds of Java projects.

Inside a base POM the following can be set up:
- Dependency and plugin versions
- Dependency and plugin dependencies, but only the bare minimum
- Profiles, for things such as deployment or testing

## Running tests

The [Surefire][surefire] and [Failsafe][failsafe] plugins take care of running tests. It is recommended using the default test search methods, which will run all the test clases with "Test" in the name as unit test, and those with "IT" as integration tests. They will be found by scanning the test packages.

### Command

To run both unit and integration tests the verify should be used:

```
mvn verify
```

## Documentation site

Maven supports its own documentation generation tool the [Maven site][maven_site], handled through the plugin of the same name.

To keep the project self contained, and take full advantage of Maven, it is recommended using this for the project's generated documentation.

By default the site is generated using an ugly and obsolete UI. For this reason a skin is provided, the [docs Maven skin][docs_maven_skin]. Using this the generated site becomes an HTML5 mobile-friendly page.

### Command

Some reports will require the output from the tests. For this reason it is recommended running all the tests before generating the site:

```
mvn verify site
```

[base_pom]: https://github.com/Bernardo-MG/base-pom
[docs_maven_skin]: https://github.com/Bernardo-MG/docs-maven-skin
[failsafe]: http://maven.apache.org/surefire/maven-failsafe-plugin/
[maven]: https://maven.apache.org/
[maven_dependency_management]: https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html#Dependency_Management
[maven_plugin_management]: https://maven.apache.org/pom.html#Plugin_Management
[maven_site]: https://maven.apache.org/plugins/maven-site-plugin/
[surefire]: http://maven.apache.org/surefire/maven-surefire-plugin/
