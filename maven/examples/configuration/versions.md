# Versions

## Properties

Always use the POM properties to define the versions.

For dependencies use the name.version scheme:

```xml
<log4j.version>2.11.0</log4j.version>
```

While plugin versions should start with plugin:

```xml
<plugin.tomcat7.version>2.2</plugin.tomcat7.version>
```

## Selectable Versions

Prepare profiles for specific dependencies sets, for example a profile for each database used:

```xml
<profile>
   <!-- H2 database profile -->
   <!-- Prepares the project to make use of an H2 in-memory database -->
   <id>h2</id>
   <dependencies>
      <dependency>
         <!-- H2 database -->
         <groupId>com.h2database</groupId>
         <artifactId>h2</artifactId>
         <version>${h2.version}</version>
      </dependency>
   </dependencies>
</profile>
```



