# Steps

## Conditional Step

```Groovy
stage('Integration tests') {
   when {
      expression {
         flowControl.runIntegrationTests()
      }
   }
   steps {
      script {
         commandRunner.integrationTests();
      }
   }
}
```

## After Step

```Groovy
stage('Integration tests') {
   steps {
      script {
         commandRunner.integrationTests();
      }
   }
   post {
      failure {
         script {
            env.ERROR_MESSAGE = "Integration tests failed";
         }
      }
      always {
         script {
           commandRunner.publishCoverage();
         }
      }
   }
}
```

## Retry

```Groovy
stage('Deploy repository'){
   steps {
      script {
         timeout(time: 30, unit: "MINUTES") {
            retry(1) {
               deployer.deployToRepo();
            }
         }
      }
   }
}
```



