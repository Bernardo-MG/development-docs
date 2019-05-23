# Ant

The Ant plugin allows running scripts as part of the Maven lifecycle:

```markup
<plugin>
   <artifactId>maven-antrun-plugin</artifactId>
   <executions>
      <execution>
         <id>initialization-scripts</id>
         <phase>initialize</phase>
         <configuration>
            <target>
               <ant antfile="${script.path}">
                  <target name="initialize" />
               </ant>
            </target>
         </configuration>
         <goals>
            <goal>run</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```



