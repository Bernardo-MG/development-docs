# Scripts

Additional scripts can be stored into files and then read by the pipeline.

## Defining Scripts

Each file should end returning itself.

```
/**
* Run unit tests.
*/
def unitTests() {
   sh "'mvn test";
}

return this;
```

## Reading Scripts

```
 stage('Setup') {
   steps {
      script {
         commandRunner = load("./ci/command.groovy");
      }
   }
}
```



