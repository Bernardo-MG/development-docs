# Setting Up

## Base POM

```xml
<parent>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-parent</artifactId>
   <version>1.4.6.RELEASE</version>
   <relativePath />
</parent>
```

## Starters

These dependencies are used to set up the application automatically.

For example this prepares a MVC project:

```xml
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

While this adds and allows running an embedded Tomcat:

```xml
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-tomcat</artifactId>
</dependency>
```

## Configuration Class

The SpringBootApplication annotation combines several configuration annotations.

```java
@SpringBootApplication
public class Application
```

For a web application:

```java
@SpringBootApplication
public class ServletApplication extends SpringBootServletInitializer
```

This should be a runnable class, meaning it requires the run method:

```java
public static void main(String[] args) {
   SpringApplication.run(Application.class, args);
}
```



