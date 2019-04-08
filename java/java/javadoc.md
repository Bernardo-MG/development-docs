---
description: Javadoc
---

# Javadoc

Java comments can be used to generate documentation. But not any comment, only those matching the [Javadoc](https://docs.oracle.com/javase/9/javadoc/javadoc.htm) specification.

```java
/**
* Returns the employee with the received code.
*
* @param id
*            employee id
* @return name of the employee with the id
*/
public String getEmployeeName(final Integer id);
```

## Generating Javadoc

It is recommended using a project management tool, such as Maven, to generate Javadocs.

But they can be built by using this command:

```bash
javadoc file.java -d [destination_path]
```

## Style Guides

* [Google's Javadoc Style Guide](https://google.github.io/styleguide/javaguide.html#s7-javadoc)

