# Environment

## Load from Maven POM

```groovy
environment {
   PROJECT_VERSION = readMavenPom().getVersion()
   PROJECT_ARTIFACT_ID = readMavenPom().getArtifactId()
   PROJECT_GROUP_ID = readMavenPom().getGroupId()
   PROJECT_NAME = readMavenPom().getName()
   REPOSITORY_URL = readMavenPom().getDistributionManagement().getRepository().getUrl()
   WAR_DEPLOYMENT_PATH = readMavenPom().getProperties().getProperty('deployment.path')
}
```

## Set Up Manually

```groovy
env.DAILY_BUILD = isDailyBuild()
```

```groovy
env.MAIL_PROJECT_NAME = "${env.JOB_NAME} [${currentBuild.number}] ${PROJECT_VERSION}"
```

