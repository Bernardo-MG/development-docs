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
final Path path;
OutputStream output;

path = Paths.get(file.getPath());

// Initialize output stream

try (final InputStream istream = new FileInputStream(file))
{
   IOUtils.copy(istream, output);
} catch (final IOException e)
{
   // Exception handling
   e.printStackTrace();
}
```

The istream will be closed no matter what happens, without explicit code. All this requires is that the resources implement the AutoCloseable interface.

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

