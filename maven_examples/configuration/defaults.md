# Defaults

These are some general tips for setting up a Maven project.

Additional configuration is described in the pages after this one.

## Settings file

Sensitive information, such as authentication data, should be moved to a [Maven settings file](https://maven.apache.org/settings.html), located in a secure path.

Then it can be loaded by Maven with any command:

```bash
mvn deploy --settings ~/settings.xml
```

## Properties

### Default Properties

Maven already contains several pre-set variables.

These are defined in the [Maven Super POM](https://maven.apache.org/pom.html#The_Super_POM).

### Additional Properties

The following properties are used by Maven plugins, and can be overwritten to set default values:

| Variable | Recommended value | Usage |
| --- | --- | --- |
| project.build.sourceEncoding | UTF-8 | Used by plugins to define the file encoding of input files |
| project.reporting.outputEncoding | UTF-8 | Used by plugins to define the file encoding of output files |
| maven.compiler.source | 1.7 | Used by the compiler plugin to define the source code version |
| maven.compiler.target | 1.7 | Used by the compiler plugin to define the generated artifacts compatibility version |
| maven.compiler.showDeprecation | true | Shows deprecation warnings on compile |
| maven.compiler.showWarnings | true | Shows compilation warnings on compile |

There are other variables which can be used, but it is not recommended changing them without a good reason:

| Variable | Usage |
| :--- | :--- |
| maven.test.skip | Set to true to disable tests |

### Array Properties

If a property contains several children they can be accessed as an array.

For example this gets the path to the first test resources directory:

```
${project.build.testResources[0].directory}
```

## Extensions

Add the [Wagon SSH](http://maven.apache.org/wagon/wagon-providers/wagon-ssh/) to allow deploying through SSH.
