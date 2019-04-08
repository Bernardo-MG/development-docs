# Deploying the WAR for Testing

Just like explained in [deploying web projects locally](https://github.com/bernardo-mg/development-docs/tree/607d3a34739325f64d3fc216771c0bc79458f781/deployment/web_locally.md), it is possible to run a web server during the integration tests, by anchoring the plugins execution to the verify phase.

## Jetty

When using the Jetty plugin with Maven use this configuration:

```markup
<plugin>
   <!-- Jetty -->
   <!-- Jetty will run the web service during the integration 
      tests -->
   <groupId>org.eclipse.jetty</groupId>
   <artifactId>jetty-maven-plugin</artifactId>
   <version>${plugin.jetty.version}</version>
   <configuration>
      <stopKey>STOP</stopKey>
      <stopPort>9999</stopPort>
      <stopWait>5</stopWait>
      <webApp>
         <contextPath>${server.test.path}</contextPath>
      </webApp>
   </configuration>
   <executions>
      <execution>
         <id>start-jetty-it</id>
         <phase>pre-integration-test</phase>
         <goals>
            <goal>start</goal>
         </goals>
         <configuration>
            <scanIntervalSeconds>0</scanIntervalSeconds>
            <daemon>true</daemon>
            <useTestScope>true</useTestScope>
            <webApp>
               <overrideDescriptor>${project.build.directory}/${project.build.finalName}/WEB-INF/web.xml</overrideDescriptor>
            </webApp>
         </configuration>
      </execution>
      <execution>
         <id>stop-jetty-it</id>
         <phase>post-integration-test</phase>
         <goals>
            <goal>stop</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

## Tomcat

When using the Tomcat plugin with Maven use this configuration:

```markup
<plugin>
   <!-- Tomcat 7 -->
   <!-- Tomcat 7 will run the web service during the integration 
      tests -->
   <groupId>org.apache.tomcat.maven</groupId>
   <artifactId>tomcat7-maven-plugin</artifactId>
   <version>${plugin.tomcat7.version}</version>
   <configuration>
      <path>${server.test.path}</path>
   </configuration>
   <executions>
      <execution>
         <id>start-tomcat-it</id>
         <phase>pre-integration-test</phase>
         <goals>
            <goal>run</goal>
         </goals>
         <configuration>
            <fork>true</fork>
            <useTestClasspath>true</useTestClasspath>
            <warSourceDirectory>${project.build.directory}/${project.build.finalName}/</warSourceDirectory>
         </configuration>
      </execution>
      <execution>
         <id>stop-tomcat-it</id>
         <phase>post-integration-test</phase>
         <goals>
            <goal>shutdown</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

