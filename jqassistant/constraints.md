# Constraints

These are validation rules, to check if the application fits into an structural criteria.

This constraint makes sure all the facades are annotated as transactional:

```markup
<constraint id="architecture:NoFacadeWithoutTransactional">
   <requiresConcept refId="architecture:Facade" />
   <description>Facade methods should me marked as transactional.
   </description>
   <cypher><![CDATA[
      MATCH
          (c:Facade:Interface)-[:DECLARES]->(m:Method { visibility: 'public' })
      WHERE
          NOT (m:Method:Spring:Transactional)
          AND NOT (m:Constructor)
      RETURN
          c.name as class,
          m.name as method
     ]]></cypher>
</constraint>
```

