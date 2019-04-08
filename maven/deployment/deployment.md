# Deployment With Maven

Maven is prepared to deploy Java artifacts. The code artifacts are deployed to an artifacts repository as part of a CI process or manually, as all it requires is calling a command:

```bash
mvn deploy
```

## Configuration

You need to tell Maven where the artifacts will be deployed. Remember that it makes a distinction between releases and snapshots, so it requires a repository for each:

```markup
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

Now they need some sort of credentials for the deployment. Never include thesein the project, instead add it to the CI configuration. It is recommended using a Maven settings file.

For the previous example the settings file would be similar to this:

```markup
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

