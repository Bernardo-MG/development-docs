# Tests

Tests are run with Junit and Maven.

## Unit and integration tests

Maven divides tests into two phases, one for unit tests and another for integration ones. Running the integration tests will run both the unit and integration tests.

In a general way, unit tests are small and fast tests, where the components use fake dependencies, or no dependencies at all. While integration tests connect several components and services.

### Commands

To run both unit and integration tests the use the following command:

```
mvn verify
```

To run only unit tests use the following command:

```
mvn test
```

### Plugins

Maven uses two plugins to take care of the tests:

- [Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/) runs unit tests.
- [Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/) runs integration tests.

Failsafe has to be set up before the tests can be run:

```
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

Some additional plugins can be used to improve testing results:

- [JaCoCo](http://eclemma.org/jacoco/trunk/doc/maven.html), generates coverage reports from Surefire and Failsafe.
- [Surefire Report](https://maven.apache.org/surefire/maven-surefire-report-plugin/), generates the unit tests report.

To set up JaCoCo use this configuration:

```
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

## Test environment

Complex test environments, which can be required by some integration tests, can be prepared with the help of Spring.

### Databases

The [JPA Example][jpa-example] uses several databases for testing, setting up a full persistence context by using Spring and Maven.

## Mocking

When preparing unit tests the dependencies should be mocked. [Mockito][mockito] is the recommended library for this.

## Using web servers with tests

Just like explained in [deploying web projects locally][deploying_locally], it is possible to run a web server during the integration tests, by anchoring the plugins execution to the verify phase.

### Jetty

When using the Jetty plugin with Maven use this configuration:

```
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
               <overrideDescriptor>${project.build.directory}/${project.artifactId}-${project.version}/WEB-INF/web.xml</overrideDescriptor>
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

```
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
            <warSourceDirectory>${project.build.directory}/${project.artifactId}-${project.version}/</warSourceDirectory>
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

[deploying_locally]: ./web_locally.md
[jpa-example]: https://github.com/Bernardo-MG/jpa-example
[mockito]: http://site.mockito.org/
