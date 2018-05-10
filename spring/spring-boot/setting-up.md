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



