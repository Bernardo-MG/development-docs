# Pruning

## Merge Duplicated Classes

```text
MATCH
   (node)
WITH
   node.fqn AS name,
   COLLECT(node) AS nodes,
   COUNT(*) AS count
WHERE
   count > 1
CALL
   apoc.refactor.mergeNodes(nodes, {mergeRels: true}) YIELD node
RETURN
   node
```

## Merge Duplicated Methods

```text
MATCH
   (class)-[:DECLARES]->(method:Method)
WITH
   class.fqn as class,
   method.name AS method,
   COLLECT(method) AS nodes,
   COUNT(*) AS count
WHERE
   count > 1
CALL
   apoc.refactor.mergeNodes(nodes, {mergeRels: true}) YIELD node
RETURN
   node
```

## Merge Duplicated Relationships

```text
MATCH
   (node)-[r]->(related)
WITH
   node.fqn AS name,
   related.fqn AS related,
   type(r) AS relType,
   COLLECT(r) AS rels,
   COUNT(*) AS count
WHERE
   count > 1
CALL
   apoc.refactor.mergeRelationships(rels) YIELD rel
RETURN
   rel
```

