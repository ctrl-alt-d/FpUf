# El llenguatge de la base de dades DML, DDL, DCL
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Les bases de dades conenen estructures per emmagatzemar informació i també contenen dades. 

A les bases de dades relacionals, per exemple, abans de emmagatzemar dades cal crear les estructures que les contindran. Si per exemple volem emmagatzemar notes d'alumnes caldrà crear les estructures 'relació d'alumnes', 'relació d'assignatures' i 'relacio de notes dels alumnes a les assignatures'. En una base de dades relacional les estructures reben el nom de 'Taules'. 

Les instruccions que creen estructures, ja siguin taules o altres tipus d'estructures com ara indexos o relacions entre talues les anomanem instruccions **DDL** ( Data Definition Language ). 

Les instruccions que maneguen dades, com ara insertar informació ( INSERT ) a les taules, esborrar-ne ( DELETE ), modificar  ( UPDATE ) o consultar ( SELECT ), les anomanem instruccions **DML** ( Data Manipulation Language ).

Per últim tenim altres instruccions que ens ajuden en el control de les transaccions, ens diuen quan comença una transacció i també com cal finalitzar-la: persistint els canvis ( COMMIT ) o bé descartant-los ( ROLLBACK ) i deixant-les dades tal com estaven. Són el **DCL**.

**Exercici apartat A**

1. Digues que fan cadascuna de les sentències SQL. ( SQL és el llenguatge de les bases de dades relacionals ).
2. Classifica en DDL, DML o DCL cada sentència SQL 
3. La sentència SELECT mostra el contingut de la relació, digues que retornaran les selects s1, s2, s4 i s4.

Sentències a treballar:

```SQL
CREATE TABLE alumnes ( DNI varchar(50), nom varchar(10000) );
CREATE INDEX idx1 ON alumnes ( nom );  --crea índex per a que les consultes per nom siguin ràpides.
BEGIN TRANSACTION tx1;
INSERT INTO alumnes VALUES ( '40404040p', 'Paquito Riquito' );
COMMIT;
SELECT * FROM alumnes;   --s1
BEGIN TRANSACTION tx2;
UPDATE alumnes SET nom = 'Polito de Lana' WHERE DNI='40404040p';
SELECT * FROM alumnes;   --s2
ROLLBACK;
SELECT * FROM alumnes;   --s3
DELETE FROM alumnes;
SELECT * FROM alumnes;   --s4
```

**Exercici apartat B**

1. Fes el mateix però ara per a una base de dades mongodb:

Sentències a treballar:

```java
db.createCollection("mycollection")
db.mycollection.ensureIndex({"name":1})
db.mycollection.insert({"name" : "MongoDB Overview"})
db.mycollection.update({"name":"MongoDB Overview"},
                       {$set:{"name":"New MongoDB Tutorial"}})
db.mycollection.find()


```




>
>######Aquest exercici està extret del llibre [Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.05.18 09:02:17
###### Editat per: daniel herrera 2016.09.27 17:26:05
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
