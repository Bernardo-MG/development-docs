# Maven Dependencies

jQAssistant is able to analyze Maven dependencies from a repository, just by including the path:

```markup
<plugin>
   <groupId>com.buschmais.jqassistant</groupId>
   <artifactId>jqassistant-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>jqassistant-scan</id>
         <goals>
            <goal>scan</goal>
         </goals>
         <configuration>
            <scanIncludes>
               <scanInclude>
                  <path>${settings.localRepository}</path>
               </scanInclude>
            </scanIncludes>
         </configuration>
      </execution>
   </executions>
</plugin>
```

But this will analyze all the dependencies stored there, which can take a really long time.

## Analyzing a Subset of Dependencies

Having this property defined:

```markup
<dependencyAnalysis.path>${project.build.directory}/jqadeps</dependencyAnalysis.path>
```

The dependencies can be copied inside that folder.

Note that they are filtered, so only those from the specified group are included, ignoring transitive dependencies.

```markup
<plugin>
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-dependency-plugin</artifactId>
   <executions>
      <execution>
         <id>dependencies-lib-folder</id>
         <goals>
            <goal>copy-dependencies</goal>
         </goals>
         <configuration>
            <outputDirectory>${dependencyAnalysis.path}</outputDirectory>
            <includeGroupIds>es.seresco</includeGroupIds>
            <includeScope>compile</includeScope>
            <classifier>sources</classifier>
            <excludeTransitive>true</excludeTransitive>
         </configuration>
      </execution>
   </executions>
</plugin>
```

Now the path can be included.

```markup
<plugin>
   <groupId>com.buschmais.jqassistant</groupId>
   <artifactId>jqassistant-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>jqassistant-scan</id>
         <goals>
            <goal>scan</goal>
         </goals>
         <configuration>
            <scanIncludes>
               <scanInclude>
                  <path>${dependencyAnalysis.path}</path>
               </scanInclude>
            </scanIncludes>
         </configuration>
      </execution>
   <executions>
<plugin>
```

