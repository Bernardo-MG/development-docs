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

## Project management

### Parent POM

Common configuration for multiple projects should be kept inside a parent POM.

These are handled just like any other dependency, and used by adding the following lines:

```
<parent>
   <groupId>com.bernardomg.maven</groupId>
   <artifactId>base-pom</artifactId>
   <version>1.2.0</version>
</parent>
```

Any project can use a parent POM. This is not a feature exclusive to multimodule projects.

A parent POM can keep common configuration for multiple projects:
- Dependency and plugin versions (plugin/dependency management nodes)
- Dependency and plugin dependencies, but only the bare minimum (plugin/dependency nodes)
- Profiles, for things such as deployment or testing

### Prepared POMs

There are a few parent POMs ready to use:
* [Base POM][base_pom], generic and useful for most projects
* [Archetype POM][archetype_pom], for Maven Archetypes

## Running tests

The [Surefire][surefire] and [Failsafe][failsafe] plugins take care of running tests.

It is recommended using the default test search methods, which will run all the test clases with "Test" in the name as unit test, and those with "IT" as integration tests. They will be found by scanning the packages in the test code folder.

### Command

To run both unit and integration tests the use the following command:

```
mvn verify
```

To run only unit tests use the following command:

```
mvn test
```

Complex test suites may require profiles. For example when testing against various databases.

## Documentation site

Maven supports its own documentation generation tool, the [Maven site][maven_site]. Which handled through the plugin of the same name.

To keep the project self contained, and take full advantage of Maven, it is recommended using this for generating the project's documentation.

By default the site is generated using an ugly and obsolete UI. For that reason the [docs Maven skin][docs_maven_skin] is used. With this theme the generated site becomes an HTML5 mobile-friendly page.

### Reports

The site includes not only documentation, but also several reports, generated along the docs.

### Command

As some reports will require the output from the tests it is recommended running all the tests before generating the site:

```
mvn verify site
```

## Linking Javadocs

Maven can generate Javadocs, but these won't link to third party libraries. This can be done by specifying the links to the Javadocs for those libraries:

```
<plugin>
   <!-- Javadoc -->
   <!-- Generates the javadocs -->
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-javadoc-plugin</artifactId>
   <configuration>
      <links>
         <link>http://docs.oracle.com/javaee/7/api/</link>
         <link>http://docs.spring.io/spring-data/commons/docs/current/api/</link>
         <link>http://docs.spring.io/spring-data/jpa/docs/current/api/</link>
         <link>http://docs.spring.io/spring-data/commons/docs/current/api/</link>
         <link>http://docs.spring.io/spring-framework/docs/current/javadoc-api/</link>
         <link>http://docs.spring.io/spring-ws/site/apidocs/</link>
      </links>
      <!-- Excludes generated code -->
      <excludePackageNames>*.generated.*</excludePackageNames>
   </configuration>
</plugin>
```

With this example, all the references to JEE7 or Spring classes will contain a link to their official Javadocs.

## Variables

### Default variables

Maven already contains several pre-set variables.

These are defined in the [Maven Super POM][maven_super_pom].

### Array variables

If a variable contains several children they can be accessed as an array.

For example this gets the path to the first test resources directory:

```
${project.build.testResources[0].directory}
```

## Archetypes

An archetype are templates for creating new Maven projects.

[archetype_pom]: https://github.com/Bernardo-MG/archetype-pom
[base_pom]: https://github.com/Bernardo-MG/base-pom

[docs_maven_skin]: https://github.com/Bernardo-MG/docs-maven-skin
[failsafe]: http://maven.apache.org/surefire/maven-failsafe-plugin/
[maven]: https://maven.apache.org/
[maven_lifecycle]: https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html
[maven_super_pom]: https://maven.apache.org/pom.html#The_Super_POM
[maven_dependency_management]: https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html#Dependency_Management
[maven_plugin_management]: https://maven.apache.org/pom.html#Plugin_Management
[maven_site]: https://maven.apache.org/plugins/maven-site-plugin/
[surefire]: http://maven.apache.org/surefire/maven-surefire-plugin/
