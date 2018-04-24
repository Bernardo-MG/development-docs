# Versions

## Properties

Always use the POM properties to define the versions.

For dependencies use the name.version scheme:

```
<log4j.version>2.11.0</log4j.version>
```

While plugin versions should start with plugin:

```
<plugin.tomcat7.version>2.2</plugin.tomcat7.version>
```

## Managing versions

Make use of POMs for setting up a global versions definition.

Prepare profiles for specific dependencies sets, for example a profile for each database used.
