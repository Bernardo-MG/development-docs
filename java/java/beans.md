---
description: Java Beans
---

# Java Beans

A specification for Java DTOs widely used for mapping data into objects.

It is used, for example, by JSON serialization and persistence libraries.

## Requirements

Java beans should:

* Have a \(explicit\) default constructor
* Contain getters and setters for all the fields
* Be serailizable

## Usage

Some libraries, such as JPA implementations, will require data objects to fit the Java Bean specification, and may add additional restrictions.

Java beans make it easy initializing objects, as they are created by the default constructor, and all the values assigned with a setter. They are used for mapping data in persistence, or when transforming JSON.

## More Information

* [Oracle's Java Bean Tutorial](https://docs.oracle.com/javase/tutorial/javabeans/)

