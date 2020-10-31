# Cassandra vs MySQL
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Un cop [instal·lat cassandra](/DAW/DAW-MP02/DAW-MP02-UF4/nosql-cassandra-getting-starting/readme.md) anem a fer un exercici de comparació d'inserció de un milió de tuples a la base de dades, insertarem a Cassandra i farem el mateix a MySQL.

*Pas 1)* Anem a crear les taules:

**DDL MySQL**:

    mysql> create table pintura (
        -> id int primary key,
        -> producte int,
        -> color int,
        -> preu int);
    Query OK, 0 rows affected (0.24 sec)
    
    mysql> create index i2 on pintura(producte);
    Query OK, 0 rows affected (0.12 sec)
    Records: 0  Duplicates: 0  Warnings: 0
    
    mysql> create index i1 on pintura(color);
    Query OK, 0 rows affected (0.07 sec)
    Records: 0  Duplicates: 0  Warnings: 0

**DDL for cassandra**:

    cqlsh:mykeyspace> create table pintura (
                  ... id int primary key,
                  ... producte int,
                  ... color int,
                  ... preu int);
    cqlsh:mykeyspace> create index i1 on pintura (producte);
    cqlsh:mykeyspace> create index i2 on pintura (color);

*Pas 2)* Preparem script per insertar dades, usarem python cql per insertar a cassandra:

**Cassandra script**:

    #!/usr/bin/python
    
    import cql
    import random
    
    db = cql.connect('localhost', 9160,  'mykeyspace', cql_version='3.0.0')
    cursor = db.cursor()
    for i in range( 1000000 ):
        producte = random.randint( 0,100 )
        color = random.randint( 0,100 )
        preu = random.randint( 100,1000 )
    
        cursor.execute('''INSERT INTO pintura (id, producte, color, preu)
                          VALUES (%s, %s, %s, %s)''' % (i, producte, color, preu))
    
        # Commit your changes in the database
        db.commit()
    
    # disconnect from server
    db.close()

**Mysql script:**

    #!/usr/bin/python
    
    import MySQLdb
    import random
    
    # Open database connection
    db = MySQLdb.connect("localhost","root","pass","test" )
    
    # prepare a cursor object using cursor() method
    cursor = db.cursor()
    
    #SQL query to INSERT a record into the table prova.
    for i in range( 1000000 ):
        producte = random.randint( 0,100 )
        color = random.randint( 0,100 )
        preu = random.randint( 100,1000 )
    
        cursor.execute('''INSERT INTO pintura (id, producte, color, preu) 
                          VALUES (%s, %s, %s, %s)''' % (i, producte, color, preu))
    
        # Commit your changes in the database
        db.commit()
    
    # disconnect from server
    db.close()


**Times**:

```bash
cc@cc-cc:~/x$ time python insert_mysql.py 

real        ??m??.???s
user        ??m??.???s
sys         ??m??.???s
```

    cc@cc-cc:~/x$ time python insert_cassandra.py 
    
    real        ??m??.???s
    user        ??m??.???s
    sys         ??m??.???s

**Exercici**

 * Realitza aquestes proves al teu ordinador i mira a quina base de dades el python inserta més ràpid.
 * Repeteix les proves, però en aquesta ocasió, en comptes d'insertar directament des de python, genera un fitxer .sql amb les comandes de seleccionar bd (o keyspace) i inserts preparades i executa'l des de la shell dels diferents SGBD. Per exemple, `time cqlsh -3 < inserts_cassandra.sql`, `time mysql -u root -p < inserts_mysql.sql`.
 * Llegeix el post [How not to benchmark Cassandra](http://www.datastax.com/dev/blog/how-not-to-benchmark-cassandra) i valora les proves que has fet.
 * Consulta quantes fileres s'han insertat a cada taula, recorda ampliar el límit quan fàcis la consulta a cassandra ( select count(*) from taula limit 9999999; )
 * Consulta quantes dades hi ha per `color = 1` i `producte = 1`
 * Pots consultar a cassandra quantes dades hi ha amb `preu = 200`? Per què?


**Ampliació**:

Segueix les instruccions de dataStax per a:

 * [Installing DataStax Community on Debian-based systems](http://www.datastax.com/documentation/cassandra/2.0/cassandra/install/installDeb_t.html) també [How to install Cassandra on Ubuntu 12.04 LTS](http://www.geroba.com/cassandra/how-to-install-cassandra-on-ubuntu-and-windows-azure/#create-vm)
 * [Initializing a multiple node cluster (single data center)](http://www.datastax.com/documentation/cassandra/2.0/cassandra/initialize/initializeSingleDS.html#task_ds_h1j_ryt_fk) Crea al menys 4 nodes.

Repeteix les proves connectant-te ara al [cluster](http://datastax.github.io/python-driver/api/cassandra/cluster.html) creat:

```python
from cassandra.cluster import Cluster
cluster = Cluster(['192.168.1.1', '192.168.1.2'])
session = cluster.connect()
...
cluster.shutdown()

```


---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2014.04.25 15:19:09
###### Editat per: daniel herrera 2014.04.30 16:34:46
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
