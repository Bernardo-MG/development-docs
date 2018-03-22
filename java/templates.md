# Project templates

[Maven archetypes][archetypes] can be used to create new projects fast.

* [Library Maven Archetype][library_archetype], meant for generic Java projects and libraries
* [Spring MVC with Thymeleaf Maven Archetype][spring_thymeleaf_archetype]

## Usage

Before using it an archetype should be downloaded from a repository. It works like any other dependency, but requires a repository with an archetypes catalog.

As an alternative it is always possible to install the archetype project locally before usage:

```
$ mvn install
```

## Setup

When creating a new archetype the [Maven Archetype Plugin][archetype_plugin] should be added to the project.

## Testing

During testing archetypes use the Maven invoker library to use themselves for creating a project. This can cause problems with embedded versions of Maven.

Check the [archetype testing goal][archetype_testing] for more information about setting up the tests.

In some cases the tests will require additional Maven configuration, such as a default profile. This can be included in a Maven settings file, defined as a property:

```
<archetype.test.settingsFile>${project.build.testResources[0].directory}/settings.xml</archetype.test.settingsFile>
```

Just by adding this property the tests will load the file located at 'src/test/resources/settings.xml' before running the tests.

[archetypes]: https://maven.apache.org/guides/introduction/introduction-to-archetypes.html
[archetype_plugin]: http://maven.apache.org/archetype/maven-archetype-plugin
[archetype_testing]: http://maven.apache.org/archetype/maven-archetype-plugin/integration-test-mojo.html

[library_archetype]: https://github.com/Bernardo-MG/library-maven-archetype
[spring_thymeleaf_archetype]: https://github.com/Bernardo-MG/spring-mvc-thymeleaf-maven-archetype
