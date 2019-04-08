# Notifications

## Send Email

```groovy
emailext (
   to: email@somewhere.com,
   subject: 'Mail subject',
   body: 'The email body'
)
```

## Email Culprits

```groovy
emailext (
   recipientProviders : [[$class: 'CulpritsRecipientProvider'],[$class: 'RequesterRecipientProvider']],
   subject: 'Warning culprits',
   body: 'The email body'
)
```

