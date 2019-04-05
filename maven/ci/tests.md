# Tests

JUnit is the usual testing library used with Maven. But as the tests are run by plugins, prepared for the usual cases, this matters little, you just need a set of tests and setting up the plugins.

## Plugins

### Surefire \(Unit Tests\)

The default testing plugin is [Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/), which runs on the testing phase:

```bash
mvn test
```

By default it scans for test classes with "Test" in their name.

### Failsafe \(Integration Tests\)

For integration test the [Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/) plugin is used. This runs on the verification phase:

```bash
mvn test
```

By default it scans for test classes with "IT" in their name.

It has to be set up before the integration tests can be run:

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

## JaCoCo \(Test Coverage\)

For test coverage you can use JaCoCo:

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

## Test Environments

Complex test environments, which can be required by some integration tests, may require profiles.

Spring can be used to set up these complex environments.

### Databases

The [JPA Example](https://github.com/Bernardo-MG/jpa-example) uses several databases for testing, setting up a full persistence context by using Spring and Maven.





