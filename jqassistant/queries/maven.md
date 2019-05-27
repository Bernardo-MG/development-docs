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

## All  the Classes in a Module

```text
MATCH
   (main:Artifact),
   (child)-[:HAS_PARENT]->(main),
   (child)-[:DESCRIBES]->(directory:Artifact:Directory),
   (directory)-[:CONTAINS]->(class:Type)
WHERE
   main.name = 'parent-module-name'
RETURN
   class.name AS class
ORDER BY
   class
```

