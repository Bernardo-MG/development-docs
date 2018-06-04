# Testing Archetypes

## Custom Configuration File

To use a custom Maven Settings file:

```xml
<properties>
   <!-- Archetype test settings -->
   <archetype.test.settingsFile>${project.build.testResources[0].directory}/settings.xml</archetype.test.settingsFile>
</properties>
```

## Custom Properties

Values for the archetype properties are added into the src/test/resources/projects/defaults/archetype.properties file. 

These will be used to set up the archetype.

## Custom Goal

The goal used on the generated project can be set in a src/test/resources/projects/defaults/goal.txt file.

## Default Values

Both the properties and goals files can be stored in the src/test/resources/projects/defaults folder, making them the default test files.



