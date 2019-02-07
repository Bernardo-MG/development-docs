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

