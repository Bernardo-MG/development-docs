# Testing Archetypes

The Maven invoker is used when testing archetype, as they need to use themselves to create a test project. This can cause problems with embedded versions of Maven.

Check the [archetype testing goal](http://maven.apache.org/archetype/maven-archetype-plugin/integration-test-mojo.html) for more information about setting up the tests.

## Custom Configuration File

In some cases the tests will require additional Maven configuration, such as a default profile. This can be included in a Maven settings file, defined as a property:

```xml
<properties>
   <!-- Archetype test settings -->
   <archetype.test.settingsFile>${project.build.testResources[0].directory}/settings.xml</archetype.test.settingsFile>
</properties>
```

Just by adding this property the tests will load the file located at 'src/test/resources/settings.xml' before running the tests.

## Custom Properties

Values for the archetype properties are added into the src/test/resources/projects/defaults/archetype.properties file. 

These will be used to set up the archetype.

```properties
groupId=com.bernardomg.test.archetype
artifactId=libraryArchetypeTest
version=1.0.0-SNAPSHOT
package=com.bernardomg.test.archetype.libraryArchetypeTest
```

## Custom Goal

The goal used on the generated project can be set in a src/test/resources/projects/defaults/goal.txt file.

```
clean package verify
```

## Default Values

Both the properties and goals files can be stored in the src/test/resources/projects/defaults folder, making them the default test files.
