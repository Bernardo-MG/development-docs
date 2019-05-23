# Maven Repositories

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

