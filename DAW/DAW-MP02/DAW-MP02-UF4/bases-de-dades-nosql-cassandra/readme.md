# Bases de dades NoSQL, Cassandra
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Llegeix les [característiques de Cassandra comparades amb un sistema gestor de base de dades relacional](http://www.ibm.com/developerworks/library/os-apache-cassandra/):

 * Relational columns are homogeneous across all rows in the table. A clear vertical relationship usually exists between data items, that is not the case with Cassandra columns. This is the reason Cassandra stores the column name with each data item (column).
 * With the relational model, 2D data space is complete. Each point in the 2D space should have at least the null value stored there. Again, this is not the case with Cassandra, and it can have rows containing only a few items, while other rows can have millions of items.
 * With a relational model, the schema is predefined and cannot be changed at runtime, while Cassandra lets users change the schema at runtime.
 * Cassandra always stores data such that columns are sorted based on their names. This makes it easier to search for data through a column using slice queries, but it is harder to search for data through a row unless you use an order-preserving partitioner.
 * Another crucial difference is that column names in RDMBS represent metadata about data, but never data. In Cassandra, however, the names of columns can include data. Consequently, Cassandra rows can have millions of columns, while a relational model usually has tens of columns.
 * Using a well-defined immutable schema, relational models support sophisticated queries that include JOINs, aggregations, and more. With a relational model, users can define the data schema without worrying about queries. Cassandra does not support JOINs and most SQL search methods. Therefore, schema has to be catered to the queries required by the application.

Llegeix també les possibles sorpreses amb Cassandra (extracte):

 * No transactions, no JOINs
 * Keys have to be unique
 * Failed operations may leave changes
 * Searching is complicated
 * Super columns and order preserving partitioners are discouraged
 * Healing from failure is manual
 * It remembers deletes

D'altre banda llegeix l'[origen de Cassandra (wikipedia)](http://en.wikipedia.org/wiki/Apache_Cassandra#History):

*Apache Cassandra was developed at Facebook to power their Inbox Search feature by Avinash Lakshman (one of the authors of Amazon's Dynamo) and Prashant Malik. It was released as an open source project on Google code in July 2008. In March 2009, it became an Apache Incubator project. On February 17, 2010 it graduated to a top-level project.*






---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2014.04.23 13:34:45
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
