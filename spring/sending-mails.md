# Sending Mails

```java
private final JavaMailSender mailSender;
```

```java
final MimeMessage mimeMessage;
final MimeMessageHelper mailMessage;
final String receiver;

mimeMessage = mailSender.createMimeMessage();
mailMessage = new MimeMessageHelper(mimeMessage, true, "UTF-8");
mailMessage.setText(contenido, true);
mailMessage.setTo(receiver);
mailMessage.setFrom(emisor);
mailMessage.setSubject(titulo);

mailSender.send(mimeMessage);
```

