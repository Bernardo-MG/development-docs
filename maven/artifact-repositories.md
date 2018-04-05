# Artifact Repositories

Artifacts should be deployed somewhere if you want them accessible.

The official Maven repository is [Maven Central](https://search.maven.org/), but deploying there can be a pain. Instead some sort of deployment platform should be used.

[Bintray](https://bintray.com) is a good option. Check their [deployment guide](https://blog.bintray.com/2014/02/11/bintray-as-pain-free-gateway-to-maven-central/) to find more about it. Once the artifacts are deployed there the repository can be synchronized with [JCenter](https://bintray.com/bintray/jcenter), and this is used as a deployment platform to publish the artifacts into Maven Central.

