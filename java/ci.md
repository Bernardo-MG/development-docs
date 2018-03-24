# Continuous integration

![CI flow][ci_flow]

Check first the [CI][ci] section.

## Travis

Continuous Integration is handled through [Travis CI][travis].

## Scripts

The CI scripts include one for setting up a Maven settings file:

```
before_script:
  # Creates Maven settings
  - ~/.scripts/java/maven/create-maven-settings.sh $VERSION_TYPE
```

This will set up the credentials for deploying the artifacts, both the JAR/WAR and the Maven site.

## Status flags

A few flags are used to control the CI flow. These are required by the [CI scripts][scripts_repo] and stored in environmental variables.


[ci]: ../general/ci.md

[ci_flow]: ../img/diagram/ci_java_activity.png
[scripts_repo]: https://github.com/Bernardo-MG/ci-shell-scripts
[travis]: https://travis-ci.org/
