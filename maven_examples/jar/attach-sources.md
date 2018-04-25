# Attach Sources

To attach sources to the JAR use this configuration:

```xml
<plugin>
   <!-- Source -->
   <!-- Bundles the source into the packaged project. -->
   <artifactId>maven-source-plugin</artifactId>
   <executions>
      <execution>
         <!-- Generates the jar for the deployment -->
         <!-- Source is bound to the package phase -->
         <id>attach-sources</id>
         <goals>
            <goal>jar-no-fork</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```



