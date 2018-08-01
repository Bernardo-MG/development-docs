# Locale

## Instantiation

### Constructor

```java
Locale locale;

locale = new Locale("fr", "CA");
```

### Builder

```java
Locale locale;

locale = new Locale.Builder().setLanguage("fr").setRegion("CA").build();
```

### Tag

Tags conforming to the IETF BCP 47 standard can be used.

```java
Locale locale;

locale = Locale.forLanguageTag("fr-CA");
```

### Constant

```java
Locale locale;

locale = Locale.CANADA_FRENCH;
```
