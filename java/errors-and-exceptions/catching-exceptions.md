# Catching Exceptions

```java
try
{
   // Code which throws exceptions
} catch (final IOException e)
{
   // Exception handling
}
```

## Finally

```java
try
{
   // Code which throws exceptions
} catch (final IOException e)
{
   // Exception handling
} finally {
   // Always runs
}
```

## Try With Resources

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

## More Information

* [The try-with-resources Statement](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html)

