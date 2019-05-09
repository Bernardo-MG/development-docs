# Groups

Aggregates constraints to apply validations.

For example this applies the constraint defined previously:

```markup
<group id="architecture:Default">
   <includeConstraint refId="architecture:NoFacadeWithoutTransactional" />
</group>
```

