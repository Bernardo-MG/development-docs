# Maven Build Plugins

Recommended Maven build plugins:

* [Ant Run](https://maven.apache.org/plugins/maven-antrun-plugin/), can handle Ant scripts.
* [Assembly](http://maven.apache.org/plugins/maven-assembly-plugin/), uilds a distributable file from all the project components.
* [Clean](https://maven.apache.org/plugins/maven-clean-plugin/), cleans the output folder.
* [Compiler](https://maven.apache.org/plugins/maven-compiler-plugin/), compiles the source code.
* [Dependency](https://maven.apache.org/plugins/maven-dependency-plugin/), copies and manipulates the project dependencies.
* [Deploy](https://maven.apache.org/plugins/maven-deploy-plugin/), takes care of the deployment phase.
* [Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/), stops the project from being built if it does not comply with a set of rules
* [Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/), runs integration tests.
* [Install](https://maven.apache.org/plugins/maven-install-plugin/), installs the project into the local Maven repository.
* [JaCoCo](http://eclemma.org/jacoco/trunk/doc/maven.html), generates coverage data from Surefire and Failsafe.
* [Jar](https://maven.apache.org/plugins/maven-jar-plugin/), generates the jar file.
* [Javadoc](https://maven.apache.org/plugins/maven-javadoc-plugin/), handles the Javadocs.
* [Release](https://maven.apache.org/maven-release/maven-release-plugin/), generates releases and updates the project.
* [Resources](https://maven.apache.org/plugins/maven-resources-plugin/), handles the project resources.
* [Site](https://maven.apache.org/plugins/maven-site-plugin/), generates the Maven Site.
* [Source](https://maven.apache.org/plugins/maven-source-plugin/), bundles the source into the packaged project.
* [Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/), runs unit tests.

These will be used by Maven, but some may require additional configuration.

Check the [archetypes](https://github.com/bernardo-mg/development-docs/tree/607d3a34739325f64d3fc216771c0bc79458f781/maven/templates.md) to find out how to set them up.

