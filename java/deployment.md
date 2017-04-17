# Java artifacts deployment

[Maven][maven] can be used to deploy Java artifacts. The JAR files are deployed to [Bintray][bintray], from there replicated into [JCenter][jcenter], and then to [Maven Central][maven_central].

Bintray has a [guide][bintray_guide] detailing how to set this up.

Once this is set up, deployment is handled through CI, which will store the deployment passkey in a safe way.

[maven]: ./maven

[bintray_guide]: https://blog.bintray.com/2014/02/11/bintray-as-pain-free-gateway-to-maven-central/

[bintray]: https://bintray.com
[jcenter]: https://bintray.com/bintray/jcenter
[maven_central]: https://search.maven.org/
