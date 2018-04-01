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

### Third party Javadocs

The generated Javadocs won't link to third party libraries. This can be fixed by specifying the links to the Javadocs for those libraries:

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
   </configuration>
</plugin>
```

With this all the references to JEE7 or Spring classes will contain a link to their official Javadocs.

### Generated code

It is recommended ignoring generated code

```
<plugin>
   <!-- Javadoc -->
   <!-- Generates the javadocs -->
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-javadoc-plugin</artifactId>
   <configuration>
      <!-- Excludes generated code -->
      <excludePackageNames>*.generated.*</excludePackageNames>
   </configuration>
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
