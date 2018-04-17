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

## Enums as Data Structures

An enum may contain additional data, for example it may store a String value.

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

## Additional Methods

Just as they can contain fields, it is possible adding any method. They behave as any other class.

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

## More Information

* [Enum Types](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html)



