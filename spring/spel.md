# SpEL

Spring Expression Language

## Acquiring a Bean

```text
#{beanName}
```

Properties can be used:

```text
#{${property.name}}
```

## Checking Properties

```text
#{'${property.name}'.contains('Some text')}
```

## Default Values

```text
${properties.booleanValue:false}
```

It may be the empty string:

```text
${properties.textValue:}
```

