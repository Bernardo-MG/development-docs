# Attach Javadocs

Again, this just needs a plugin, in this case the [Maven Javadoc plugin](https://maven.apache.org/plugins/maven-javadoc-plugin/):

```xml
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

## Third party Javadocs

The generated Javadocs won't link to third party libraries. This can be fixed by specifying the links to the Javadocs for those libraries:

```xml
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

## Ignoring code

Some code is generated automatically and its Javadocs won't add anything. This is a good case for ignoring code during Javadoc generation:

```xml
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
