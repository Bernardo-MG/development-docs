# Structure

## Types extending a base type, along the base type

```text
MATCH
   (component:Type {name: 'ClassName'}),
   (extension:Type)-[:EXTENDS|IMPLEMENTS*0..]->(component)
RETURN
   extension
```

## Methods, including inherited methods, of a class

```text
MATCH
   (component:Type {name: 'CrudService'}),
   (component)-[:EXTENDS|IMPLEMENTS*0..]->()-[:DECLARES]->(inheritedMethod:Method)
RETURN
   component,
   inheritedMethod
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
   service.name AS service,
   method.name AS method,
   extract(p in apoc.text.regexGroups(annotationValue.value, "\\('([a-zA-Z]*)', '[crud]'\\)") | p[1]) as permission
```

## Methods In a Maven Module

```text
MATCH
   (artifact:Artifact {name :'module-name'}),
   (artifact)-[:CONTAINS*..]->(class:Class)
RETURN
   artifact.name AS artifact,
   class.name AS class
```

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

