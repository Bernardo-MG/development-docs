---
description: Errors and Exceptions in Java
---

# Errors and Exceptions

There are three kinds of exception:

* Checked exceptions, which should be caught
* Runtime exceptions, application exceptions which can't be predicted and need not to be caught
* Errors, for problems from outside the application scope

## Throwing Exceptions

Any class which extends from Throwable can be thrown:

```java
throw new Exception();
```

This can be done at any point. But checked exceptions will need to be caught or declared.

## Exceptions and Flow Control

Exceptions should be used to handle exceptional cases. Not for flow control.

## More Information

* [Exceptions](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html)

