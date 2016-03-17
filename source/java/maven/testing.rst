==================
Testing with Maven
==================

Maven supports unit and integration tests as part of the project lifecycle.

But to take full advantage of this a few additional dependencies are required,
first of all the `Surefire`_ and `Failsafe`_ plugins, as these will run test in the
unit and integration testing phases. But also a testing framework, `TestNG`_, is
needed to run the actual tests.

Configuration
=============

Two test suites are included in the projects, one for unit tests, and another for
integration ones. These can be found in the test resources folders under the
names tests_maven_unit_suite.xml and tests_maven_integration_suite.xml.

These are TestNG test suites, and just point to the unit and integration tests
base folder.

Setting an integration servlet container
========================================

If a servlet container is required as part of the integration tests the Jetty
or the Tomcat plugins can be used.

To set up the Jetty plugin just use this configuration:

.. code-block:: xml

    <plugin>
        <!-- Jetty -->
        <!-- Jetty will run the web service during the integration tests -->
        <groupId>org.eclipse.jetty</groupId>
        <artifactId>jetty-maven-plugin</artifactId>
        <version>${plugin.jetty.version}</version>
        <configuration>
            <stopKey>STOP</stopKey>
            <stopPort>9999</stopPort>
            <stopWait>5</stopWait>
            <webApp>
                <contextPath>${server.test.path}</contextPath>
            </webApp>
            <contextXml>${project.build.outputDirectory}/jetty/jetty.xml</contextXml>
        </configuration>
        <executions>
            <execution>
                <id>start-jetty-it</id>
                <phase>pre-integration-test</phase>
                <goals>
                    <goal>start</goal>
                </goals>
                <configuration>
                    <scanIntervalSeconds>0</scanIntervalSeconds>
                    <daemon>true</daemon>
                </configuration>
            </execution>
            <execution>
                <id>stop-jetty-it</id>
                <phase>post-integration-test</phase>
                <goals>
                    <goal>stop</goal>
                </goals>
            </execution>
        </executions>
    </plugin>

- :download:`IT Jetty configuration file <../../_downloads/maven/jetty.xml>`

This will run the verify target and the project will be running in a Jetty
server during the integration tests.

.. _Surefire: https://maven.apache.org/surefire/maven-surefire-plugin/
.. _Failsafe: https://maven.apache.org/surefire/maven-failsafe-plugin/
.. _TestNG: http://testng.org/