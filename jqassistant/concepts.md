# Concepts

Concepts are queries used to change the data structure.

This for example tags all the facade services in the application:

```markup
<concept id="architecture:Facade">
   <description>Labels all facades as such</description>
   <cypher><![CDATA[
      MATCH
          (c:Type)
      WHERE
          c.fqn STARTS WITH "org.company"
          AND c.fqn CONTAINS "facade"
      SET
          c:Facade
      RETURN
          c
     ]]></cypher>
</concept>
```

