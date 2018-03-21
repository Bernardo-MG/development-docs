# Java artifacts deployment

## JAR/WAR

[Maven][maven] is used to deploy Java artifacts. The JAR files are deployed to [Bintray][bintray], from there replicated automatically into [JCenter][jcenter], and manually to [Maven Central][maven_central].

Bintray has a [guide][bintray_guide] detailing how to set this up.

Deployment is handled through CI. This will require a passkey, which should be stored in an environmental variable.

### Command

If needed, a project can be deployed manually:

```
mvn deploy
```

### Configuration

Add the repositories info to the POM:

```
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

```
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

## Documentation deployment

Maven is used to generate and deploy a Maven site, which works as the project documentation site.

A static content server is used to store the files. Any which supports SSH can be used. Do not use FTP as it is unsecure.

Deployment is handled through CI. This will require authentication data, which should be stored in environmental variables.

### Command

The Maven site can be deployed with:

```
mvn site site:deploy
```

### Configuration

Like with the JAR, the Maven site requires a server:

```
<distributionManagement>
   <site>
      <id>site</id>
      <name>Project Development Documentation Site</name>
      <url>[deployment_url]</url>
   </site>
</distributionManagement>
```

And authentication data in the settings file:

```
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

[bintray]: https://bintray.com
[jcenter]: https://bintray.com/bintray/jcenter
[maven_central]: https://search.maven.org/

[maven]: ./maven

[bintray_guide]: https://blog.bintray.com/2014/02/11/bintray-as-pain-free-gateway-to-maven-central/
