# Manifest

The manifest file includes metadata about the project, and can be used for example by repositories.

This is added by setting up the [Maven Jar plugin](https://maven.apache.org/plugins/maven-jar-plugin/):

```xml
<plugin>
   <!-- Jar -->
   <!-- Generates the jar file. -->
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-jar-plugin</artifactId>
   <configuration>
      <archive>
         <index>true</index>
         <manifest>
            <addClasspath>true</addClasspath>
            <addDefaultImplementationEntries>true</addDefaultImplementationEntries>
            <addDefaultSpecificationEntries>true</addDefaultSpecificationEntries>
            <packageName>${project.groupId}</packageName>
         </manifest>
         <manifestEntries>
            <name>${manifest.name}</name>
            <url>${project.url}</url>
         </manifestEntries>
      </archive>
   </configuration>
</plugin>
```

The manifest data should contain the artifact coordinates as a folder:

```xml
<properties>
   <!-- Manifest data -->
   <manifest.name>com/bernardomg/maven/pom/base</manifest.name>
</properties>
```



