# Git

jQAssistant can analyze the contents of a Git repository.

```text
<plugin>
   <!-- JQAssistant -->
   <!-- Code and architecture analysis. -->
   <groupId>com.buschmais.jqassistant</groupId>
   <artifactId>jqassistant-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>jqassistant-scan</id>
         <goals>
            <goal>scan</goal>
            <goal>analyze</goal>
         </goals>
         <configuration>
            <scanIncludes>
               <scanInclude>
                  <path>${project.basedir}/.git</path>
               </scanInclude>
            </scanIncludes>
         </configuration>
      </execution>
   </executions>
   <dependencies>
      <dependency>
         <groupId>de.kontext-e.jqassistant.plugin</groupId>
         <artifactId>jqassistant.plugin.git</artifactId>
         <version>${plugin.jqassistant.git.version}</version>
      </dependency>
   </dependencies>
</plugin>
```

