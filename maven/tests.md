# Tests

Tests are run with Junit and Maven.

## Unit and Integration Tests

Maven divides tests into two phases, one for unit tests and another for integration ones. Running the integration tests will run both the unit and integration tests.

In a general way, unit tests are small and fast tests, where the components use fake dependencies, or no dependencies at all. While integration tests connect several components and services.

It is recommended using the default test search methods, which will run all the test clases with "Test" in the name as unit test, and those with "IT" as integration tests. They will be found by scanning the packages in the test code folder.

### Commands

To run both unit and integration tests the use the following command:

```bash
mvn verify
```

To run only unit tests use the following command:

```bash
mvn test
```

### Plugins

Maven uses two plugins to take care of the tests:

* [Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/) runs unit tests.
* [Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/) runs integration tests.

Some additional plugins can be used to improve testing results:

* [JaCoCo](http://eclemma.org/jacoco/trunk/doc/maven.html), generates coverage reports from Surefire and Failsafe.
* [Surefire Report](https://maven.apache.org/surefire/maven-surefire-report-plugin/), generates the unit tests report.

