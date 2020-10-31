# Bases de dades distribuides: replicació i particionat
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Quan un SGBD està rodant a la vegada en vàries màquines independent i de manera transparent als usuaris que s'hi connecten, estem parlant de base de dades distribuida.

Aquesta distribució, no és pas transparent per a l'administrador i per als desenvolupadors d'aplicacions. Aquests conèixen exactament quines dades hi ha a cadascun dels nodes que conformen la base de dades distribuida.

En les distribució de dades hi ha dos conceptes claus que cal conèixer:

* *Replicació* Dades que estan replicades, estan a la vegada en més d'un node.

* *Particionat* Les dades d'una col·lecció o d'una relació estan repartides entre els nodes del sistema de base de dades distribuit segons algun criteri.

**Exercicis**:

* Imagina una base de dades de 100Milions de registres. Quina desaventatge té la replicació vs el particionat?
* Una base de dades amb 100Milions de registres la repliquem entre 10 nodes que estan a 10 ciutats diferents. Com creus que això repercuteix en les operacions de lectura que fan els usuaris? I a les operacions d'escriptura?
* MS SQLServer permet al desenvolupador crear taules a diferents SGBD i crear una vista sobre aquestes taules per a presentar-la als usuaris ( o més ben dit a les aplicacions que fan servir els usuaris ) com si d'una sola taula es tractés. Les sentències SQL per a fer aquestes operacions són de fàcil lectura i interpretació, mira de comprendre-les:

Instruccions SQL:

```sql
-- Al servidor 1:
CREATE TABLE clients_33
  (CustomerID   INTEGER PRIMARY KEY
                CHECK (id_del_client BETWEEN 1 AND 32999),
  ... -- Additional column definitions)

-- Al servidor 2:
CREATE TABLE clients_66
  (CustomerID   INTEGER PRIMARY KEY
                CHECK (id_del_client BETWEEN 33000 AND 65999),
  ... -- Additional column definitions)

-- Al servidor 3:
CREATE TABLE clients_99
  (CustomerID   INTEGER PRIMARY KEY
                CHECK (id_del_client BETWEEN 66000 AND 99999),
  ... -- Additional column definitions)


CREATE VIEW Clients AS
   SELECT * FROM CompanyDatabase.TableOwner.clients_33
UNION ALL
   SELECT * FROM Server2.CompanyDatabase.TableOwner.clients_66
UNION ALL
   SELECT * FROM Server3.CompanyDatabase.TableOwner.clients_99
```

*Nota: exemple adaptat de la web de TechNet de Microsoft: https://technet.microsoft.com/en-us/library/ms188299(v=sql.105).aspx

* En un sistema de base de dades distribuit la taula de clients està repartida entre diferentes nodes, semblant a l'exemple anterior, de manera que els usuaris tingui les dades dels seus clients més properes. Per quin camp de `client` podriem fer aquest particionat? Hi ha increment de rendiment? Hi ha increment de disponibilitat de dades? Per què?
* A la documentació de Mongodb trobem informació de com ha de ser un [cluster en producció](https://docs.mongodb.com/manual/core/sharded-cluster-architectures-production/) i com pot ser un [cluster en test](https://docs.mongodb.com/manual/core/sharded-cluster-architectures-test/): *In a production cluster, you must ensure that data is redundant and that your systems are highly available.*. Preguntes: que significa 'producció' i 'test'? Per què calen dos entorns? Per què diu Mongodb que és necessària la redundància? 



>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>



---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.06.19 14:12:13
###### Editat per: daniel herrera 2016.08.30 16:52:24
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
