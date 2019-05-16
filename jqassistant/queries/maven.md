# Maven

## Number of internal module dependencies

```text
MATCH
   (main:Maven:Main)-[r:DEPENDS_ON]->(dependency:Maven:Main)
RETURN
   main.name AS module,
   COUNT(r) AS dependenciesCount,
   COLLECT(dependency.name) AS dependencies
ORDER BY
   dependenciesCount DESC,
   module
```

