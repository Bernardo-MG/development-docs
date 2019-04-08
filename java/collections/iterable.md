# Iterable

Root interface for collections which allows iterating them.

## Traversing

It can be iterated:

```java
Iterator<String> itr;

itr = strings.iterator();

while(itr.hasNext()) {
   System.out.println(itr.next());
}
```

And it can be used in for-each loops:

```java
for(String s : strings) {
   System.out.println(s);
}
```

