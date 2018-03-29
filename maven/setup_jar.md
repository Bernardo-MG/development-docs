# Setting up the JAR

## Attach sources

To attach sources to the JAR use this configuration:

```
<plugin>
   <!-- Source -->
   <!-- Bundles the source into the packaged project. -->
   <artifactId>maven-source-plugin</artifactId>
   <executions>
      <execution>
         <!-- Generates the jar for the deployment -->
         <!-- Source is bound to the package phase -->
         <id>attach-sources</id>
         <goals>
            <goal>jar-no-fork</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

## Attach Javadocs

To attach javadocs to the JAR use this configuration:

```
<plugin>
   <!-- Javadoc -->
   <!-- Handles the Javadocs. -->
   <artifactId>maven-javadoc-plugin</artifactId>
   <executions>
      <!-- Javadoc plugin is bound to the deploy phase -->
      <execution>
         <!-- Generates the Javadocs for the deployment -->
         <id>attach-javadocs</id>
         <goals>
            <goal>jar</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

## Manifest

To set up the JAR manifest use this configuration.

```
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

```
<properties>
   <!-- Manifest data -->
   <manifest.name>com/bernardomg/maven/pom/base</manifest.name>
</properties>
```
