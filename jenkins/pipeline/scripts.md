# Scripts

Additional scripts can be stored into files and then read by the pipeline.

## Defining Scripts

Each file should end returning itself.

```Groovy
/**
* Run unit tests.
*/
def unitTests() {
   sh "'mvn test";
}

return this;
```

## Reading Scripts

```Groovy
stage('Setup') {
   steps {
      script {
         commandRunner = load("./ci/command.groovy")
      }
   }
}
```

## Using Scripts

```Groovy
stage('Unit tests') {
    steps {
        script { commandRunner.unitTests() }
    }
}
```



