# Routing

## Hash Routing

When using a JS client it is possible to use an alternative to normal routing by letting the client itself handle URL changes.

This is done by adding a hash to the URL:

> https:\\somewhere.com\\#path

Anything after the hash will be handled by the client, while the path before the hash will be handled by the server.

Useful when:

* The server-side code is not accesible
* The server can't handle URL redirects
* Deploying to static file servers

In other cases it is better to avoid this, as anything after the hash is not meant to be sent to the server, and web parsers, such as crawlers, will ignore it. In practice it breaks the URL.

