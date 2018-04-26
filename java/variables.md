# Variables

## Static/class Variables

Single instance which is shared by all the classes. Sort of a global variable bound to the class where it is defined.

Try to use them as final, which makes them into constants.

```java
public class SomeClass {

   public static final String constantValue = "Some text";

}
```

## Instance Variables

Each instance of the class will have their own copy of the variable.

```java
public class SomeClass {

   private String value = "some value";

}
```

## Local Variables

Declared inside methods:

```java
public final void someMethod() {
   final String value = "some value";
}
```

## Parameters

Received by methods:

```java
public final void someMethod(final String value)
```

## More Information

* [Java Variables](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html)



