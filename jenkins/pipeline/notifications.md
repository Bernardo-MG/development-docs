# Notifications

## Send Email

```Groovy
emailext (
   to: email@somewhere.com,
   subject: "Mail subject",
   body: "The email body"
)
```

## Email Culprits

```Groovy
emailext (
   recipientProviders : [[$class: 'CulpritsRecipientProvider'],[$class: 'RequesterRecipientProvider']],
   subject: "Warning culprits",
   body: "The email body"
)
```



