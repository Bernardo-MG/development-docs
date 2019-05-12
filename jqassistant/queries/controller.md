# Controller

## Controller Paths

```text
MATCH
   (controller:Controller)-[:ANNOTATED_BY]->(controllerAnnotation:Annotation)-[:OF_TYPE]->(controllerAnnotationType:Type),
   (controller)-[:DECLARES]->(method:Method),
   (method)-[:ANNOTATED_BY]->(annotation:Annotation)-[:OF_TYPE]->(annotationType:Type),
   (controllerAnnotation)-[:HAS]->(controllerAnnotationValue:Value)-[:CONTAINS]->(controllerValues)
WHERE
   NOT method:Constructor
   AND controllerAnnotationType.fqn STARTS WITH 'org.springframework.web.bind.annotation'
   AND controllerAnnotationValue.name IN ['value', 'path']
   AND controllerAnnotationType.name IN ['RequestMapping', 'PostMapping', 'GetMapping', 'PutMapping', 'DeleteMapping']
   AND annotationType.fqn STARTS WITH 'org.springframework.web.bind.annotation'
   AND annotationType.name IN ['RequestMapping', 'PostMapping', 'GetMapping', 'PutMapping', 'DeleteMapping']
WITH
   controller,
   method,
   annotation,
   controllerValues,
   annotationType
OPTIONAL MATCH
   (annotation)-[hasValue:HAS]->(annotationValue:Value)-[:CONTAINS]->(values)
WHERE
   annotationValue.name IN ['value', 'path']
RETURN
   controller.name AS controller,
   method.name AS method,
   controllerValues.value AS controllerPath,
   COALESCE(values.value, "") AS methodPath,
   annotationType.name AS annotation
ORDER BY
   controller,
   method
```

