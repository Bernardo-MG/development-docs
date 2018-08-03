# Internationalization Formatting

The following can require formatting:

* Texts
* Dates
* Numbers
* Currencies

## Texts

### Compound Messages

Having this message bundle:

```
template = The employee {0} has the id {1,number,integer}
```

```java
ResourceBundle messages;
Object[] messageArguments;
MessageFormat formatter;
String formatted;

messages = ResourceBundle.getBundle("MessageBundle", currentLocale);

messageArguments = {
   "John",
   new Integer(12)
};

formatter = new MessageFormat("");
formatter.applyPattern(messages.getString("template"));

formatted = formatter.format(messageArguments);
```

### Plurals

Having this message bundle:

```properties
template = There {0}.
noEmployees = are no employees
oneEmployee = is one employee
multipleEmployees = are {1} employees
```

```java
ResourceBundle messages;
Object[] messageArguments;
Object[] choices;
double[] numbers;
MessageFormat formatter;
ChoiceFormat choiceForm;
String formatted;
Format[] formats;

messages = ResourceBundle.getBundle("MessageBundle", currentLocale);

numbers = {0,1,2};
choices = {
   bundle.getString("noEmployees"),
   bundle.getString("oneEmployee"),
   bundle.getString("multipleEmployees")
};

choiceForm = new ChoiceFormat(numbers, choices);

formatter = new MessageFormat("");
formatter.applyPattern(messages.getString("template"));

formats = {choiceForm, NumberFormat.getInstance()};
formatter.setFormats(formats);

messageArguments = {2, 3};

formatted = formatter.format(messageArguments);
```

Which will print "There are 3 employees"

## Dates

```java
DateFormat dateFormatter;
Date today;
String formatted;

dateFormatter = DateFormat.getDateInstance(DateFormat.DEFAULT, currentLocale);
today = new Date();
formatted = dateFormatter.format(today);
```

## Numbers

```java
NumberFormat numberFormatter;
String formatted;

numberFormatter = NumberFormat.getNumberInstance(currentLocale);
formatted = numberFormatter.format(number);
```

For percentages:

```java
NumberFormat percentFormatter;
String formatted;

percentFormatter = NumberFormat.getPercentInstance(currentLocale);
formatted = percentFormatter.format(percent);
```

## Currencies

```java
NumberFormat currencyFormatter;
String formatted;

currencyFormatter = NumberFormat.getCurrencyInstance(currentLocale);
formatted = currencyFormatter.format(amount);
```

## Patterns

### Date Patterns

```java
DateFormat dateFormatter;
Date today;
String formatted;

dateFormatter = new SimpleDateFormat("EEE d MMM yy", currentLocale);
today = new Date();
formatted = dateFormatter.format(today);
```

### Numeric Patterns

```java
DecimalFormat patternFormatter;
String formatted;

patternFormatter = new DecimalFormat("###.##");
formatted = patternFormatter.format(amount);
```

## More Information

* [Formatting](https://docs.oracle.com/javase/tutorial/i18n/format/index.html)



