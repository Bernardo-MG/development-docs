# Continuous Integration

![CI flow][ci_flow]

Check first the [CI][ci] section.

## Travis

Continuous Integration is handled through [Travis CI][travis].

## Scripts

There is a [CI script][scripts_repo] for setting up a Maven settings file:

```
before_script:
  # Creates Maven settings
  - ~/.scripts/java/maven/create-maven-settings.sh $VERSION_TYPE
```

This will set up the credentials for deploying the artifacts, both the JAR/WAR and the Maven site.

For this to work two profiles are needed, one for deploying release artifacts and another for development artifacts:

```
<profile>
   <!-- Release site deployment profile -->
   <!-- Sets the site repository to point to the releases repo -->
   <id>deployment-release</id>
   <activation>
      <!-- Active by default so the repository appears in the reports -->
      <activeByDefault>true</activeByDefault>
   </activation>
   <distributionManagement>
      <site>
         <id>site</id>
         <name>Project Documentation Site</name>
         <!-- The URL should be set externally -->
         <url>${site.release.url}</url>
      </site>
   </distributionManagement>
</profile>
<profile>
   <!-- Development site deployment profile -->
   <!-- Sets the site repository to point to the development repo -->
   <id>deployment-development</id>
   <distributionManagement>
      <site>
         <id>site-development</id>
         <name>Project Development Documentation Site</name>
         <!-- The URL should be set externally -->
         <url>${site.develop.url}</url>
      </site>
   </distributionManagement>
</profile>
```

The site URLs properties are handled by the Maven settings script.

A third deployment profile is used when deploying all the artifacts:

```
after_success:
  # Documentation deployment script
  - ~/.scripts/java/maven/deploy-site.sh $DO_DEPLOY_DOCS deployment
  # Code artifacts deployment script
  - ~/.scripts/java/maven/deploy.sh $DO_DEPLOY deployment
```

```
<profile>
   <!-- Deployment profile -->
   <!-- Sets ups the environment for deployment -->
   <id>deployment</id>
   <properties>
      <!-- Tests are skipped -->
      <maven.test.skip>true</maven.test.skip>
   </properties>
</profile>
```

## Status flags

A few flags are used to control the CI flow. These are required by the CI scripts and stored in environmental variables.


[ci]: ../general/ci.md

[ci_flow]: ../img/diagram/ci_java_activity.png
[scripts_repo]: https://github.com/Bernardo-MG/ci-shell-scripts
[travis]: https://travis-ci.org/
