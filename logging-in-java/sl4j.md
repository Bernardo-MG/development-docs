# SL4J

[Logging facade](https://www.slf4j.org/), which hides the actual logging library being used.

## Usage

```java
public class LoginHandler {

   private static final Logger logger = LoggerFactory.getLogger(LoginHandler.class);

   public void login(String user) {
      logger.debug("User {} logged in", user);
   }

}
```

## Logging Levels

Levels are defined by the Logger interface.

* Trace
* Debug
* Info
* Warn
* Error

