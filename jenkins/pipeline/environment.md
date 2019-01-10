# Environment

## Load from Maven POM

```Groovy
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

```Groovy
env.DAILY_BUILD = isDailyBuild();
```



