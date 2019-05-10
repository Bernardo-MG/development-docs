# Detecting Problems

## Circular dependencies

```text
MATCH
    (t:Type)-[:DEPENDS_ON*]->(t)
RETURN
    t
```

## Entities used in facade services

```text
MATCH
	(facade:Facade)-[:DECLARES]->(method),
	(method)-[:HAS]->()-[:OF_TYPE*]->(receivedtype:Entity),
	(method)-[:RETURNS]->(returntype:Entity)
WHERE
	(method.visibility="public" OR method.visibility="protected")
RETURN
	facade.name AS service,
    method.name AS method,
    collect(distinct receivedtype.name) AS received,
    returntype.name AS returned
```

## Controllers with public final methods

```text
MATCH (c:Controller)-[:DECLARES]->(m:Method { visibility: 'public' })
WHERE
    EXISTS(m.final)
RETURN
    c.name as controller,
    m.name as method
```

