# Configuration

These are some general tips for setting up a Maven project.

Additional configuration is described in the pages after this one.

## Properties

The following properties when set will used by Maven plugins:

|Variable|Recommended value|Usage|
|---|---|---|
|project.build.sourceEncoding|UTF-8|Used by plugins to define the file encoding of input files|
|project.reporting.outputEncoding|UTF-8|Used by plugins to define the file encoding of output files|
|maven.compiler.source|1.7|Used by the compiler plugin to define the source code version|
|maven.compiler.target|1.7|Used by the compiler plugin to define the generated artifacts compatibility version|
|maven.compiler.showDeprecation|true|Shows deprecation warnings on compile|
|maven.compiler.showWarnings|true|Shows compilation warnings on compile|

## Extensions

Add the [Wagon SSH][wagon_ssh] to allow deploying through SSH.

[wagon_ssh]: http://maven.apache.org/wagon/wagon-providers/wagon-ssh/
