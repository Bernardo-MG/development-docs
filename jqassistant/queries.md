# Queries

As it makes use of a Neo4j database queries can be made by using Cypher. The data is enriched by applying any concept defined in the rules files.

For example this finds all the controllers inside a Spring application with public final methods:

```text
MATCH (c:Controller)-[:DECLARES]->(m:Method { visibility: 'public' })
WHERE 
    EXISTS(m.final)
RETURN 
    c.name as controller, 
    m.name as method
```

This returns all methods annotated with PreAuthorize and the permission used:

```text
MATCH
    (service:Type)-[:DECLARES]->(method:Method),
    (method:Method)-[:ANNOTATED_BY]->(annotation:Annotation)-[:OF_TYPE]->(annotationType:Type),
    (annotation:Annotation)-[:HAS]->(annotationValue:Value{name:"value"})
WHERE
    annotationType.fqn = "org.springframework.security.access.prepost.PreAuthorize"
RETURN
    service.name as service,
    method.name as method,
    extract(p in apoc.text.regexGroups(annotationValue.value, "\\('([a-zA-Z]*)', '[crud]'\\)") | p[1]) as permission
```

