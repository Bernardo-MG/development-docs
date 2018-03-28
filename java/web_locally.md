# Deploying Web Projects Locally

## Maven

Maven can deploy web applications locally by using plugins.

First of all define a property for the deployment context:

```
<properties>
   <server.path>/webproject</server.path>
</properties>
```

This will be used to deploy the project into the http://localhost:8080/webproject/ URL.

### Jetty

When using the [Jetty plugin][jetty_plugin] with Maven use this configuration:

```
<plugin>
   <!-- Jetty -->
   <groupId>org.eclipse.jetty</groupId>
   <artifactId>jetty-maven-plugin</artifactId>
   <version>${plugin.jetty.version}</version>
   <configuration>
      <stopKey>STOP</stopKey>
      <stopPort>9999</stopPort>
      <stopWait>5</stopWait>
      <webApp>
         <contextPath>${server.path}</contextPath>
      </webApp>
   </configuration>
</plugin>
```

### Tomcat

When using the [Tomcat plugin][tomcat_plugin] with Maven use this configuration:

```
<plugin>
   <!-- Tomcat 7 -->
   <groupId>org.apache.tomcat.maven</groupId>
   <artifactId>tomcat7-maven-plugin</artifactId>
   <version>${plugin.tomcat7.version}</version>
   <configuration>
      <path>${server.path}</path>
   </configuration>
</plugin>
```

[jetty_plugin]: https://www.eclipse.org/jetty/documentation/9.4.x/jetty-maven-plugin.html
[tomcat_plugin]: http://tomcat.apache.org/maven-plugin-2.0/tomcat7-maven-plugin/
