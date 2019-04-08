---
description: Errors and Exceptions in Java
---

# Errors and Exceptions

There are three kinds of exception:

* Checked exceptions, which should be caught
* Runtime exceptions, application exceptions which can't be predicted and need not to be caught
* Errors, for problems from outside the application scope

## Checked Exceptions

They should caught:

```java
try
{
   // This can cause an exception
   in = new FileInputStream(file);
} catch (final IOException e)
{
   // Exception handling
   e.printStackTrace();
} finally
{
   // Always applied
   file.delete();
}
```

Or declared:

```java
public handleFile(final File file) throws IOException;
```

### Try With Resources

To make sure the resources are always closed or finalized there is the try-with-resources variant, since Java 7:

```java
try (final ServletOutputStream outputStream = response.getOutputStream();)
{
   // Write to output stream
   if (output instanceof ByteArrayOutputStream)
   {
      ((ByteArrayOutputStream) output).writeTo(outputStream);
   }

   output.flush();
   output.close();
} catch (final IOException e)
{
   // Exception handling
   e.printStackTrace();
}
```

This way the outputStream will be closed always, not matter what happens. All it requires is that the resources implement the AutoCloseable interface.

## Throwing Exceptions

Any class which extends from Throwable can be thrown:

```java
throw new Exception();
```

This can be done at any point. But checked exceptions will need to be caught or declared.

## Chaining Exceptions

It is possible to answer an exception with another:

```java
try
{
   // Code which can thow an exception
} catch (final IOException e)
{
   throw new RuntimeException(e);
}
```

In this case a checked exception is transformed into a runtime exception. These are chained exceptions, and Throwable offers methods to travel through the chain or exceptions.

## Exceptions and Flow Control

Exceptions should be used to handle exceptional cases. Not for flow control.

## More Information

* [Exceptions](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html)

