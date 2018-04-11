---
description: JPQL
---

# JPQL

With the Java Persistence Query Language the persistence objects graph can be queried, in a similar way to querying a database by using SQL, and it looks just like that.

```
SELECT c FROM Customer c JOIN c.orders o WHERE c.status = 1 AND o.totalPrice > 10000
```

## Integration

JPQL can be used by any JPA implementation, replacing other query languages.



