# Documentation Deployment

In a similar fashion the Javadocs and a Maven site can be deployed:

```bash
mvn site site:deploy
```

## Configuration

First of all include a site configuration:

```xml
<distributionManagement>
   <site>
      <id>site-development</id>
      <name>Project Development Documentation Site</name>
      <!-- The URL should be set externally -->
      <url>${site.develop.url}</url>
   </site>
</distributionManagement>
```

It is a good idea hiding the actual deployment URL, as in some cases it can give too much information. It can be loaded from the settings file during CI.

As with the artifacts deployment we will need some access settings:

```xml
<settings>
   <servers>
      <server>
         <id>site-development</id>
         <username>[username]</username>
         <password>[password]</password>
      </server>
   </servers>
</settings>
```
