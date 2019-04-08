# Regular Expression

## String

The String class contains support for regular expressions:

```java
Boolean matches;

matches = string.matches(regex);
```

The following methods support regular expressions:

* matches
* split
* replaceFirst
* replaceAll

## Regex Model

The JDK includes classes for regular expressions. These are the Pattern and the Matcher.

The Pattern contains the regular expression, while the Matcher is used to apply said regular expression.

```java
String numbers;
Pattern pattern;
Matcher matcher;
String text;

text = "123";

numbers = "[0-9]*";
pattern = Pattern.compile(numbers);
matcher = pattern .matcher(text);
```

Now you can work with the matcher.

```java
Boolean matches;

matches = mat.matches();
```

