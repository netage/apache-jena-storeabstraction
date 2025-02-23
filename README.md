# apache-jena-storeabstraction
Abstraction layer to provide DataSource like functionality for Apache Jena Sparql endpoints

If you create a Java application running in an application container like e.g. Tomcat and you need database access you configure a DataSource.
This allows you to define on container level the connection settings through a DataSource. The connection is established through the JDBC driver configured on the DataSource.
It allows a level of abstraction between the Java application and a backend database.

For RDF Graph stores, there is no equivalent of a DataSource, so you'll need to create the connections to the SPARQL endpoints in all you applications.

## Store Abstraction Layer
This store abstraction layer aims at solving this problem by allowing you to define a `<Resource/>` block in your configuration. You can then access the defined resource through a JNDI lookup and get a Object implementing a AbstractStore interface. You'll program against the abstract store interface, using SPARQL queries or SPARQL Graph Store Protocol abstraction.

The actual implementation for your graph store abstraction will take care of the connection to the specific backend.
this allows you to easily swap out graph stores for your application without touching the code.
