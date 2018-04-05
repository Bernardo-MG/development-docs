# Deployment With Maven

## JAR/WAR

[Maven](./maven) is used to deploy Java artifacts. The code artifacts are deployed to an artifacts repository as part of the CI process.

### Command

If needed, a project can be deployed manually:

```bash
mvn deploy
```

### Configuration

Add the repositories info to the POM:

```xml
<distributionManagement>
   <repository>
      <uniqueVersion>false</uniqueVersion>
      <id>releases</id>
      <name>Releases Repository</name>
      <url>[deployment_url]</url>
   </repository>
   <snapshotRepository>
      <uniqueVersion>false</uniqueVersion>
      <id>snapshots</id>
      <name>Snapshots Repository</name>
      <url>[snapshots_deployment_url]</url>
   </snapshotRepository>
</distributionManagement>
```

The 'repository' node defines the releases repository, while the 'snapshotRepository' defines the snapshots one.

They will require access data. Never include it in the project, instead add it to the CI configuration. It is recommended using a Maven settings file.

For the previous example the settings file would require something like:

```xml
<settings>
   <servers>
      <server>
         <id>releases</id>
         <username>[username]</username>
         <password>[password]</password>
      </server>
      <server>
         <id>snapshots</id>
         <username>[username]</username>
         <password>[password]</password>
      </server>
   </servers>
</settings>
```



