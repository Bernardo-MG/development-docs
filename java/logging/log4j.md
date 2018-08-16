# Log4j

[Logging library from Apache](https://logging.apache.org/log4j/)

## Templated Messages

```java
logger.debug("Logging in user {}", user.getName());
```

## Formatted Messages

These can be formatted with the use of Java's formatter:

```java
Logger logger = LogManager.getFormatterLogger("Foo");

logger.debug("Logging in user %s", user.getName());
```

## Logging Levels

Levels are defined by the Level class.

* All
* Finest
* Finer
* Fine
* Config
* Info
* Warning
* Severe
* Off



