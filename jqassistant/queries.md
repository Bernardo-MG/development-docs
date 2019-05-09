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

