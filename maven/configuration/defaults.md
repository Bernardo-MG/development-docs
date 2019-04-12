# Default Properties

The [Maven Super POM](https://maven.apache.org/pom.html#The_Super_POM) includes several default properties.

### Array Properties

If a property contains several children they can be accessed as an array.

For example this gets the path to the first test resources directory:

```text
${project.build.testResources[0].directory}
```

### Properties to Override

The following properties should be set up to match the project requirements:

| Variable | Recommended value | Usage |
| :--- | :--- | :--- |
| project.build.sourceEncoding | UTF-8 | Used by plugins to define the file encoding of input files |
| project.reporting.outputEncoding | UTF-8 | Used by plugins to define the file encoding of output files |
| maven.compiler.source | 1.7 | Used by the compiler plugin to define the source code version |
| maven.compiler.target | 1.7 | Used by the compiler plugin to define the generated artifacts compatibility version |
| maven.compiler.showDeprecation | true | Shows deprecation warnings on compilation |
| maven.compiler.showWarnings | true | Shows compilation warnings on compilation |

### Flow Properties

These properties have an impact in the Maven flow. Don't override them without having a good reason.

| Variable | Usage |
| :--- | :--- |
| maven.test.skip | Set to true to disable tests |

