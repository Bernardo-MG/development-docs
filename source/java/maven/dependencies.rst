============
Dependencies
============

The versions of all the dependencies should be declared on the properties section
of the POM, following the format 'dependency.version'.

For example, if the project requires using Hibernate then it would be declared as
this:

.. code-block:: xml

    <properties>
        <!-- Dependencies versions -->
        ...
        <hibernate.version>5.1.0.Final</hibernate.version>
        ...
    </properties>

    <dependencies>
        ...
        <dependency>
            <!-- Hibernate Entity Manager -->
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-core</artifactId>
            <version>${hibernate.version}</version>
        </dependency>
        ...
    </dependencies>

Plugins are to be handled in a similar way:

.. code-block:: xml

    <properties>
        <!-- Plugins versions -->
        ...
        <plugin.changes.version>2.11</plugin.changes.version>
        ...
    </properties>

    <plugins>
        ...
        <plugin>
            <!-- Changes -->
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-changes-plugin</artifactId>
            <version>${plugin.changes.version}</version>
            ...
        </plugin>
        ...
    </plugins>