# SOAP

XML-based messages for web services. Can be used for asynchronous messaging.

It is obsolete, preffer JSON messages with REST over this.

## Validation

As these messages are based on XML they can be validated as usual. This is actually one of its strongest points, but can be problematic, as the client message may contain minor errors which are easy to fix.

It is recommended enforcing full validation to messages sent, but reducing it to the minimum for messages received.

## WSDL

Web services consuming SOAP may offer a WSDL contract, which defines the communication constraints.
