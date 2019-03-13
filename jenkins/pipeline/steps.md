# Steps

## Conditional Step

```Groovy
stage('Integration tests') {
   when {
      expression { flowControl.runIntegrationTests() }
   }
   steps {
      script { commandRunner.integrationTests() }
   }
}
```

## Retry

```Groovy
stage('Deploy repository'){
   steps {
      script {
         timeout(time: 30, unit: 'MINUTES') {
            retry(1) {
               deployer.deployToRepo();
            }
         }
      }
   }
}
```

## After Step

In this case a message is stored in an environmental variable, and then it always publishes the coverage results.

```Groovy
stage('Integration tests') {
   steps {
      script { commandRunner.integrationTests() }
   }
   post {
      failure {
         script { env.ERROR_MESSAGE = 'Integration tests failed' }
      }
      always {
         script { commandRunner.publishCoverage() }
      }
   }
}
```

## After All the Steps

```Groovy
post {
    failure {
        script { notifier.notifyFailure(currentBuild) }
    }
    changed {
        script { notifier.notifyChange(currentBuild) }
    }
}
```



