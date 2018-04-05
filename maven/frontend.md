# Frontend With Maven

While Maven is not particularly well suited for frontend technologies such as Javascript, there are many plugins which can ease working with them.

Just remember that Maven is mainly a Java tool, and any other technology should be a secondary aspect of the project. When the frontend moves away from Java it is best to split the project in two.

## Webjars

[Webjars](http://www.webjars.org/) are frontend dependencies packaged into Jars.

The downside is that they require a specific framework, such as Spring or Play, to be usable. Check their documentation for more details.

## Minification

To minify JS and CSS files use the [Minify Maven Plugin](http://samaxes.github.io/minify-maven-plugin/).

### CSS

```xml
<plugin>
   <!-- Minify -->
   <!-- Minifies files. -->
   <groupId>com.samaxes.maven</groupId>
   <artifactId>minify-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>minify-css</id>
         <phase>package</phase>
         <configuration>
            <cssSourceDir>resources/css</cssSourceDir>
            <cssSourceIncludes>
               <cssSourceInclude>**</cssSourceInclude>
            </cssSourceIncludes>
            <cssFinalFile>style.css</cssFinalFile>
         </configuration>
         <goals>
            <goal>minify</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

### Javascript

```xml
<plugin>
   <!-- Minify -->
   <!-- Minifies files. -->
   <groupId>com.samaxes.maven</groupId>
   <artifactId>minify-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>minify-js</id>
         <configuration>
            <jsSourceIncludes>
               <jsSourceInclude>**</jsSourceInclude>
            </jsSourceIncludes>
            <jsSourceExcludes>
               <jsSourceExclude>initialize.js</jsSourceExclude>
            </jsSourceExcludes>
            <jsFinalFile>scripts.js</jsFinalFile>
         </configuration>
         <goals>
            <goal>minify</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

## Javascript validation

Use the [JSHint plugin](https://github.com/cjdev/jshint-mojo) to validate Javascript files.

```xml
<plugin>
   <!-- JSHint -->
   <!-- Validates Javascript files. -->
   <groupId>com.cj.jshintmojo</groupId>
   <artifactId>jshint-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>jshint</id>
         <phase>test</phase>
         <goals>
            <goal>lint</goal>
         </goals>
      </execution>
   </executions>
   <configuration>
      <options>maxdepth:3,latedef,nonew,jquery</options>
      <directories>
         <directory>src/main/webapp/resources/js</directory>
      </directories>
      <reporter>checkstyle</reporter>
      <reportFile>target/jshint.xml</reportFile>
      <failOnError>true</failOnError>
   </configuration>
</plugin>
```

## npm and Webpack

Some project may have advanced requirements, such as additional dependencies, which only npm and webpack can handle.

For these cases the [Frontend Maven plugin](https://github.com/eirslett/frontend-maven-plugin) can be used.

### npm

```xml
<plugin>
   <!-- Frontend Plugin -->
   <!-- Manages frontend dependencies -->
   <groupId>com.github.eirslett</groupId>
   <artifactId>frontend-maven-plugin</artifactId>
   <configuration>
      <installDirectory>target</installDirectory>
   </configuration>
   <executions>
      <execution>
         <id>node-npm-install</id>
         <goals>
            <goal>install-node-and-npm</goal>
         </goals>
         <configuration>
            <nodeVersion>${plugin.frontend.node.version}</nodeVersion>
            <npmVersion>${plugin.frontend.npm.version}</npmVersion>
         </configuration>
      </execution>
      <execution>
         <id>npm-install</id>
         <goals>
            <goal>npm</goal>
         </goals>
         <configuration>
            <arguments>install</arguments>
         </configuration>
      </execution>
   </executions>
</plugin>
```

It is recommended binding a npm testing script to the testing phase:

```xml
<plugin>
   <!-- Frontend Plugin -->
   <groupId>com.github.eirslett</groupId>
   <artifactId>frontend-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>npm-test</id>
         <goals>
            <goal>npm</goal>
         </goals>
         <phase>test</phase>
         <configuration>
            <arguments>test</arguments>
         </configuration>
      </execution>
   </executions>
</plugin>
```

### npm and webpack:

```xml
<plugin>
   <!-- Frontend Plugin -->
   <groupId>com.github.eirslett</groupId>
   <artifactId>frontend-maven-plugin</artifactId>
   <configuration>
      <installDirectory>target</installDirectory>
   </configuration>
   <executions>
      <execution>
         <id>node-npm-install</id>
         <goals>
            <goal>install-node-and-npm</goal>
         </goals>
         <configuration>
            <nodeVersion>${plugin.frontend.node.version}</nodeVersion>
            <npmVersion>${plugin.frontend.npm.version}</npmVersion>
         </configuration>
      </execution>
      <execution>
         <id>npm-install</id>
         <goals>
            <goal>npm</goal>
         </goals>
         <configuration>
            <arguments>install</arguments>
         </configuration>
      </execution>
      <execution>
         <id>webpack</id>
         <goals>
            <goal>webpack</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

If needed, webpack can receive environmental variables:

```xml
<plugin>
   <!-- Frontend Plugin -->
   <groupId>com.github.eirslett</groupId>
   <artifactId>frontend-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>webpack</id>
         <goals>
            <goal>webpack</goal>
         </goals>
         <configuration>
            <environmentVariables>
               <NODE_ENV>${node.env}</NODE_ENV>
               <APP_VERSION>${node.env.appVersion}</APP_VERSION>
               <APP_ROUTE>${node.env.rootRoute}</APP_ROUTE>
               <REPO_URL>${node.env.repoUrl}</REPO_URL>
               <INPUT_PATH>${node.env.inputPath}</INPUT_PATH>
               <OUTPUT_PATH>${node.env.outputPath}</OUTPUT_PATH>
               <MODULE_PATH>${node.env.modules}</MODULE_PATH>
            </environmentVariables>
         </configuration>
      </execution>
   </executions>
</plugin>
```



