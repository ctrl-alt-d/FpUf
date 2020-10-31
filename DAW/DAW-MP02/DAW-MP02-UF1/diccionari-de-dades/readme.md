# Diccionari de dades
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Més endavant s'estudiarant les 12 regles del Dr Codd: *Codd's Twelve Commandments*. Per ara introduim la regla número 4 que ens diu el següent:

>**Rule 4: Dynamic online catalog based on the relational model:**
>
>The data base description is represented at the logical level in the same way as ordinary data, so that authorized users can apply the same relational language to its interrogation as they apply to the regular data.

**Explicació introducció**

Anem a suposar que hem creat una estructura a la base de dades anomenada 'relació d'alumnes' amb les columnes 'DNI' i 'nom'. Sabem que podem fer una consulta a la base de dades ( SELECT ) i que ens digui quins alumnes tenim emmagatzemats en aquesta relació tot mostrant-nos el DNI i el NOM de cada alumne. 

**Explicació de la regla**

El que ens diu aquesta regla és que podem fer servir aquest mateix llenguatge d'interrogació a la base de dades ( SELECT ) per saber quines estructures conté la base de dades. És a dir, per saber quines relacions hem creat ( saber que la base de dades conté, per exemple i entre altres, la 'relació d'alumnes' ) i quines columnes cotenen aquestes relacions. Per tant, el sistema gestor de base de dades ens ofereix unes taules que contenen aquesta informació.

**Oracle metadata**

La Wikipedia a l'article 'Oracle metadata' ens diu el següent:

*The Oracle Database contains tables which describe what database objects – i.e. tables, procedures, triggers etc. – exist within the database. This information about the information is known as metadata.*

*Oracle metadata is information contained within the Oracle Database about the objects contained within the Oracle database. You can use this information to find all tables accessible by a user, get a list of stored procedures, and get information about many other types of objects in an Oracle database.*

**Exercicis**

1) Treballa el concepte de metadata que ens defineix la wikipedia. Estigues segur que entens que la metadata és el diccionari de dades i que aquest es presenta en forma de taules ja predefinides al SGBD.

2) Que són aquests noms de taules? Completa la descripió dels dos que falten.

*    `ALL_TABLES` – 
*    `ALL_VIEWS` – list of all views in the current database that are accessible to the current user
*    `ALL_TAB_COLUMNS` – 
*    `ALL_ARGUMENTS` – lists the arguments of functions and procedures that are accessible to the current user
*    `ALL_ERRORS` – lists descriptions of errors on all stored objects (views, procedures, functions, packages, and package bodies) that are accessible to the current user
*    `ALL_OBJECT_SIZE` – included for backward compatibility with Oracle version 5
*    `ALL_PROCEDURES` – (from Oracle 9 onwards) lists all functions and procedures (along with associated properties) that are accessible to the current user
*    `ALL_SOURCE` – describes the text (i.e. PL/SQL) source of the stored objects accessible to the current user
*    `ALL_TRIGGERS` – list all the triggers accessible to the current user

3) Què ens retornaran aquestes sentències:

Sentència 1:

```sql
SELECT
  TABLE_NAME
FROM
  ALL_TABLES
WHERE
  TABLE_NAME LIKE '%alumnes%'
ORDER
  BY TABLE_NAME;
```


Sentència 2:

```sql
SELECT
  TABLE_NAME,
  COLUMN_NAME
FROM
  ALL_TAB_COLUMNS
WHERE
  TABLE_NAME LIKE '%alumnes%'
```

4) Observa aquesta pregunta i resposta de l'stackoverflow: [Get all table names of a particular database by SQL query?](http://stackoverflow.com/questions/3913620/get-all-table-names-of-a-particular-database-by-sql-query) i contesta la següent pregunta tot argumentant-ho: Creus que està normalitzat en nom de les taules i columnes que conformen el diccionari de dades? 

>
>######Aquest exercici està extret del llibre [Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>

5) Quina creus que és la importàcia de disposar d'un diccionari de dades?

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.05.18 09:25:03
###### Editat per: daniel herrera 2017.09.29 14:08:53
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
