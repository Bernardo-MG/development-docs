# Parent POM

Use a parent POM to hold the configuration required by all the projects, avoiding complex hierarchies.

In those rare cases where you need a very specific POM, for example for Maven Archetypes, make use of a specialized POM, while trying to keep all the configuration in a single file. Each project will extend this configuration to fit their specific needs, for example by setting up the project artifact as a WAR.

## Managed vs Explicit

Should a parent POM include dependencies. Depends on the aim, if the POM is completely generic then it won't need dependencies beyond Maven plugins, but if it is meant to enforce a configuration it may require dependencies set.

### Dependencies

If you need to enforce versions make use of the dependency management, preferring BOMs. Otherwise add the dependencies, but this will mean all the projects will include those dependencies, no matter if they use them or not.

### Plugins

First of all remember that Maven by default makes use of several plugins, and all of them shouldh have their versions enforced in the plugin management.

For example, the assembly plugin:

```xml
<pluginManagement>
   <plugin>
      <!-- Assembly -->
      <!-- Builds a distributable file from all the project components. -->
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-assembly-plugin</artifactId>
      <version>${plugin.assembly.version}</version>
   </plugin>
</pluginManagement>
```

Otherwise, does all your project need that plugin? If you are going to run integration tests it makes sense forcing the projects to use the Failsafe plugin:

```xml
<build>
   <plugin>
      <!-- Failsafe -->
      <!-- Runs integration tests. -->
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-failsafe-plugin</artifactId>
      <executions>
         <!-- Failsafe is bound to the integration-test and verify 
            phases -->
         <execution>
            <id>failsafe-integration-tests</id>
            <goals>
               <goal>integration-test</goal>
            </goals>
         </execution>
         <execution>
            <id>failsafe-verify</id>
            <goals>
               <goal>verify</goal>
            </goals>
         </execution>
      </executions>
   </plugin>
</build>
```

Optional plugins should be left in the plugin management. Your POM may be designed for JAR projects, but if you set up the WAR plugin the final user will be able to reuse it for his web project.

## Example

These are a few parent POMs ready to use:

* [Base POM](https://github.com/Bernardo-MG/base-pom), generic and useful for most projects
* [Archetype POM](https://github.com/Bernardo-MG/archetype-pom), for Maven Archetypes



