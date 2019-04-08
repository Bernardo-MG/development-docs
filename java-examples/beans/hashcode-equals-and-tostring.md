# Hashcode, equals and toString

## equals

JDK:

```java
public final boolean equals(final Object obj) {
   if (this == obj) {
      return true;
   }

   if (obj == null) {
      return false;
   }

   if (getClass() != obj.getClass()) {
      return false;
   }

   final CompositeKey other = (CompositeKey) obj;
   return Objects.equals(id, other.id)
         && Objects.equals(name, other.name);
}
```

Apache Commons:

```java
public final boolean equals(final Object obj) {
   return EqualsBuilder.reflectionEquals(this, obj, false);
}
```

## hashCode

JDK:

```java
public final int hashCode() {
    return Objects.hash(id, supportId);
}
```

Apache Commons:

```java
public final int hashCode() {
   return HashCodeBuilder.reflectionHashCode(this);
}
```

## toString

Guava:

```java
public final String toString() {
   return MoreObjects.toStringHelper(this).add("id", id).add("name", name).toString();
}
```

Apache Commons:

```java
public final String toString() {
   return ToStringBuilder.reflectionToString(this);
}
```

