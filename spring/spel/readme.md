# SpEL

Spring Expression Language

## Acquiring a Bean

```
#{beanName}
```

Properties can be used:

```
#{${property.name}}
```

## Checking Properties

```
#{'${property.name}'.contains('Some text')}
```

## Default Values

```
${properties.booleanValue:false}
```

It may be the empty string:

```
${properties.textValue:}
```



