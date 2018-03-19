# Java artifacts deployment

[Maven][maven] is used to deploy Java artifacts. The JAR files are deployed to [Bintray][bintray], from there replicated automatically into [JCenter][jcenter], and manually to [Maven Central][maven_central].

Bintray has a [guide][bintray_guide] detailing how to set this up.

Deployment is handled through CI. This will require a passkey, which should be stored in an environmental variable.

## Documentation deployment

Maven is used to generate and deploy a Maven site, which works as the project documentation site.

A static content server is used to store the files. Any which supports SSH can be used. Do not use FTP as it is unsecure.

Deployment is handled through CI. This will require authentication data, which should be stored in environmental variables.

[maven]: ./maven

[bintray_guide]: https://blog.bintray.com/2014/02/11/bintray-as-pain-free-gateway-to-maven-central/

[bintray]: https://bintray.com
[jcenter]: https://bintray.com/bintray/jcenter
[maven_central]: https://search.maven.org/
