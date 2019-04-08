# Maven Reports

Recommended Maven report plugins:

* [Changes](https://maven.apache.org/plugins/maven-changes-plugin/), generates the changes report from the changes log.
* [Checkstyle](https://maven.apache.org/plugins/maven-checkstyle-plugin/), checks that the source files comply with style standards.
* [Dependency](https://maven.apache.org/plugins/maven-dependency-plugin/), generates the dependencies analysis report.
* [FindBugs](http://gleclaire.github.io/findbugs-maven-plugin/), checks for patterns which are prone to errors.
* [JaCoCo](http://eclemma.org/jacoco/trunk/doc/maven.html), generates coverage reports from Surefire and Failsafe.
* [JDepend](http://www.mojohaus.org/jdepend-maven-plugin/), generates the dependencies report.
* [Javadoc](https://maven.apache.org/plugins/maven-javadoc-plugin/), generates the Javadocs.
* [JXR](http://maven.apache.org/jxr/maven-jxr-plugin/), generates references to the source files, used by other reports.
* [OWASP Dependency Check](https://jeremylong.github.io/DependencyCheck/), searches for dependencies with known vulnerabilities.
* [PMD](https://maven.apache.org/plugins/maven-pmd-plugin/), checks that the code complies with a series of code quality rules.
* [Project Info](https://maven.apache.org/plugins/maven-project-info-reports-plugin/), generates general information reports.
* [Site](https://maven.apache.org/plugins/maven-site-plugin/), generates the Maven Site.
* [Surefire Report](https://maven.apache.org/surefire/maven-surefire-report-plugin/), generates the unit tests report.
* [Taglist](http://www.mojohaus.org/taglist-maven-plugin/), generates a report of all the temporal tags still on the code.

These will be generated along the [Maven Site](http://maven.apache.org/guides/mini/guide-site.html).

The OWASP Dependency Check is very slow, so it is not recommended generating it with each build.

Check the [archetypes](https://github.com/bernardo-mg/development-docs/tree/607d3a34739325f64d3fc216771c0bc79458f781/maven/templates.md) to find out how to set them up.

