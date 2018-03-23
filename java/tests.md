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
