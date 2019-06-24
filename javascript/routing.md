# Routing

## Hash Routing

When using a JS client it is possible to use an alternative to normal routing by letting the client itself handle URL changes.

This is done by adding a hash to the URL:

> https:\\somewhere.com\\#path

It is useful when the page is deployed to a static content server, but otherwise it is better to avoid this, as it will break the URL.

