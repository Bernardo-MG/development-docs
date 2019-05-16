# Maven

## Number of internal module dependencies

```text
MATCH
   (main:Maven:Main)-[r:DEPENDS_ON]->(:Maven:Main)
RETURN
   main.name AS module,
   COUNT(r) AS dependencies
ORDER BY
   dependencies DESC,
   module
```

