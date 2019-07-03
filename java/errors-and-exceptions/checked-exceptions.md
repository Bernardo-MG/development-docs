# Checked Exceptions

They should be caught:

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

