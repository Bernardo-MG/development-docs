---
description: Java Enums
---

# Enums

This data structure allows defining a set of values, and assigning them to an object.

```java
public enum NumbersEnum {

    /**
     * First enum value.
     */
    ONE,
    /**
     * Third enum value.
     */
    THREE,
    /**
     * Second enum value.
     */
    TWO

}
```

```java
NumbersEnum number = NumbersEnum.TWO;
```

## Enums as Classes

Java enums work similar to any class, which means they can implement interfaces, and contain custom methods.

## Enums as Data Structures

As they are similar to other classes they can be used to create data structures, for example each value may contain a String:

```java
public enum StringEnum
{

   VALUE("StringValue")

   private String content;

   private StringEnum(final String content)
   {
      this.content = content;
   }

   public String getContent()
   {
      return content;
   }

}
```

As enum constructors should be private, there is no way to create a value which is not contained in the enum.

## Switchs

Enums are easy to use in switchs:

```java
public void checkValue(final NumbersEnum value) {
   switch(value) {
   case ONE:
      // Code
      break;
   case TWO:
      // Code
      break;
   default:
   }
}
```

## Finding Values

Enums contain all the fields defined on them, and these can be acquired easily:

```java
NumbersEnum.values();
```

Working with the ordinal value is not recommended, as this will change of the fields are reordered:

```java
NumbersEnum.TWO.ordinal();
```

It is better using the string value:

```java
final NumbersEnum numbers = NumbersEnum.valueOf("TWO");
```

## More Information

* [Enum Types](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html)

