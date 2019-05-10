# Structure

## Types extending a base type

```text
MATCH
    (component:Type {name: 'ClassName'}),
    (extension:Type)-[:EXTENDS|IMPLEMENTS*0..]->(component)
RETURN
    extension
```

## Methods annotated with PreAuthorize and the permission used

```text
MATCH
    (service:Type)-[:DECLARES]->(method:Method),
    (method:Method)-[:ANNOTATED_BY]->(annotation:Annotation)-[:OF_TYPE]->(annotationType:Type),
    (annotation:Annotation)-[:HAS]->(annotationValue:Value{ name:'value' })
WHERE
    annotationType.fqn = 'org.springframework.security.access.prepost.PreAuthorize'
RETURN
    service.name as service,
    method.name as method,
    extract(p in apoc.text.regexGroups(annotationValue.value, "\\('([a-zA-Z]*)', '[crud]'\\)") | p[1]) as permission
```



