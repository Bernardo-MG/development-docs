---
description: Deploying Documentation with Maven
---

# Deploying Documentation

Maven is used to generate and deploy a Maven site, which works as the project documentation site.

A static content server is used to store the files. Any which supports SSH can be used. Do not use FTP as it is unsecure.

Deployment is handled through CI. This will require authentication data, which should be stored in environmental variables.

## Command

The Maven site can be deployed with:

```bash
mvn site site:deploy
```

## Configuration

Like deploying the JAR, the Maven site requires a server:

```xml
<distributionManagement>
   <site>
      <id>site</id>
      <name>Project Development Documentation Site</name>
      <url>[deployment_url]</url>
   </site>
</distributionManagement>
```

And authentication data in the settings file:

```xml
<settings>
   <servers>
      <server>
         <id>site</id>
         <username>[username]</username>
         <password>[password]</password>
      </server>
   </servers>
</settings>
```



