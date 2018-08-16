# Tests

Tests are run with Junit and Maven.

## Plugins

### Failsafe

Failsafe has to be set up before the tests can be run:

```xml
<plugin>
   <!-- Failsafe -->
   <!-- Runs integration tests. -->
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-failsafe-plugin</artifactId>
   <executions>
      <!-- Failsafe is bound to the integration-test and verify 
         phases -->
      <execution>
         <id>failsafe-integration-tests</id>
         <goals>
            <goal>integration-test</goal>
         </goals>
      </execution>
      <execution>
         <id>failsafe-verify</id>
         <goals>
            <goal>verify</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

### JaCoCo

To set up JaCoCo use this configuration:

```xml
<plugin>
   <!-- JaCoCo -->
   <!-- Generates coverage data from Surefire and Failsafe. -->
   <groupId>org.jacoco</groupId>
   <artifactId>jacoco-maven-plugin</artifactId>
   <executions>
      <!-- Jacoco is bound to the initialize and verify phases -->
      <execution>
         <id>jacoco-initialize</id>
         <goals>
            <goal>prepare-agent</goal>
         </goals>
      </execution>
      <execution>
         <id>jacoco-test-report</id>
         <goals>
            <goal>report</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

## Test Environment

Complex test environments, which can be required by some integration tests, may require profiles.

Spring can be used to set up these complex environments.

### Databases

The [JPA Example](https://github.com/Bernardo-MG/jpa-example) uses several databases for testing, setting up a full persistence context by using Spring and Maven.

## Mocking

When preparing unit tests the dependencies should be mocked. [Mockito](http://site.mockito.org/) is the recommended library for this.

## Using Web Servers with Tests

Just like explained in [deploying web projects locally](./web_locally.md), it is possible to run a web server during the integration tests, by anchoring the plugins execution to the verify phase.

### Jetty

When using the Jetty plugin with Maven use this configuration:

```xml
<plugin>
   <!-- Jetty -->
   <!-- Jetty will run the web service during the integration 
      tests -->
   <groupId>org.eclipse.jetty</groupId>
   <artifactId>jetty-maven-plugin</artifactId>
   <version>${plugin.jetty.version}</version>
   <configuration>
      <stopKey>STOP</stopKey>
      <stopPort>9999</stopPort>
      <stopWait>5</stopWait>
      <webApp>
         <contextPath>${server.test.path}</contextPath>
      </webApp>
   </configuration>
   <executions>
      <execution>
         <id>start-jetty-it</id>
         <phase>pre-integration-test</phase>
         <goals>
            <goal>start</goal>
         </goals>
         <configuration>
            <scanIntervalSeconds>0</scanIntervalSeconds>
            <daemon>true</daemon>
            <useTestScope>true</useTestScope>
            <webApp>
               <overrideDescriptor>${project.build.directory}/${project.build.finalName}/WEB-INF/web.xml</overrideDescriptor>
            </webApp>
         </configuration>
      </execution>
      <execution>
         <id>stop-jetty-it</id>
         <phase>post-integration-test</phase>
         <goals>
            <goal>stop</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

### Tomcat

When using the Tomcat plugin with Maven use this configuration:

```xml
<plugin>
   <!-- Tomcat 7 -->
   <!-- Tomcat 7 will run the web service during the integration 
      tests -->
   <groupId>org.apache.tomcat.maven</groupId>
   <artifactId>tomcat7-maven-plugin</artifactId>
   <version>${plugin.tomcat7.version}</version>
   <configuration>
      <path>${server.test.path}</path>
   </configuration>
   <executions>
      <execution>
         <id>start-tomcat-it</id>
         <phase>pre-integration-test</phase>
         <goals>
            <goal>run</goal>
         </goals>
         <configuration>
            <fork>true</fork>
            <useTestClasspath>true</useTestClasspath>
            <warSourceDirectory>${project.build.directory}/${project.build.finalName}/</warSourceDirectory>
         </configuration>
      </execution>
      <execution>
         <id>stop-tomcat-it</id>
         <phase>post-integration-test</phase>
         <goals>
            <goal>shutdown</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```


