---
description: Javadoc
---

# Javadoc

Java comments can be used to generate documentation. But not any comment, only those matching the [Javadoc](https://docs.oracle.com/javase/9/javadoc/javadoc.htm) specification.

It is using Javadocs in all the code, and validating it as part of the CI process.

## Generating Javadoc

It is recommended using a project management tool, such as Maven, to generate Javadocs.

But they can be built by using this command:

```bash
javadoc file.java -d [destination_path]
```

## Style Guides

* [Google's Javadoc Style Guide](https://google.github.io/styleguide/javaguide.html#s7-javadoc)



