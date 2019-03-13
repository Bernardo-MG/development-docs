# Commands

## Running Tests

```shell
mvn clean verify
```

With multimodule project the testing process will be stopped once a module fails. To avoid this there is the "fail at end" property:

```shell
mvn clean verify -fae
```

Tests on modules depending on the failed module won't run, but all the other modules will have their tests executed.

## Checking for Updates

To check if there are newer versions for the dependencies use the following command:

```shell
mvn versions:display-dependency-updates versions:display-plugin-updates
```

## Generating Site

```shell
mvn clean site
```

## Purging Dependencies

Sometimes you need to delete and download again all the dependencies. This may be caused by the use of snapshots.

This command will do so:

```
mvn dependency:purge-local-repository
```

To remove only snapshots:

```
mvn dependency:purge-local-repository -DsnapshotsOnly=true
```



