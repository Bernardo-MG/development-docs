# Logging

## Logging Queries

```markup
<Logger name="org.hibernate.SQL" level="debug" additivity="false">
   <AppenderRef ref="console" />
</Logger>

<Logger name="org.hibernate.type.descriptor.sql" level="trace" additivity="false">
   <AppenderRef ref="console" />
</Logger>
```

## Logging Statistics

Statistics can be activated with  the following property:

```markup
<property name="hibernate.generate_statistics" value="true"/>
```

Then they can be logged:

```markup
<Logger name="org.hibernate.stat" level="debug" additivity="false">
   <AppenderRef ref="console" />
</Logger>

<Logger name="org.hibernate.engine.internal.StatisticalLoggingSessionEventListener" level="info" additivity="false">
   <AppenderRef ref="console" />
</Logger>
```

This will generate the following log:

```text
INFO  | o.h.e.i.StatisticalLoggingSessionEventListener     258  | Session Metrics {
    5298200 nanoseconds spent acquiring 1 JDBC connections;
    0 nanoseconds spent releasing 0 JDBC connections;
    5711500 nanoseconds spent preparing 7 JDBC statements;
    30328100 nanoseconds spent executing 6 JDBC statements;
    97972900 nanoseconds spent executing 1 JDBC batches;
    0 nanoseconds spent performing 0 L2C puts;
    0 nanoseconds spent performing 0 L2C hits;
    0 nanoseconds spent performing 0 L2C misses;
    100573600 nanoseconds spent executing 1 flushes (flushing a total of 15 entities and 0 collections);
    0 nanoseconds spent executing 0 partial-flushes (flushing a total of 0 entities and 0 collections)
}
```

