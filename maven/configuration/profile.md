# Profiles

```markup
<profiles>
   <profile>
      <!-- Release deployment profile -->
      <!-- Sets the site repository to point to the releases repo -->
      <id>deployment-release</id>
      <activation>
         <!-- Active by default so the repository appears in the reports -->
         <activeByDefault>true</activeByDefault>
      </activation>
      <distributionManagement>
         <site>
            <id>site</id>
            <name>Project Documentation Site</name>
            <!-- The URL should be set externally -->
            <url>${site.release.url}</url>
         </site>
      </distributionManagement>
   </profile>
<profiles>
```

## Applying Profile

```bash
mvn package -Pdeployment-release
```

