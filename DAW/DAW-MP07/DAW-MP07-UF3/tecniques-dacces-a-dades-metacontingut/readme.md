# Tècniques d’accés a dades. Metacontingut.
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
### 1. Desenvolupa aplicacions d'accés a magatzems de dades, aplicant mesures per mantenir la seguretat i la integritat de la informació. 
#### 1.1 S'han analitzat les tecnologies que permeten l'accés mitjançant programació a la informació disponible en magatzems de dades.

* [PHP - Accés a dades](/DAW/DAW-MP07/DAW-MP07-UF3/php-acces-a-dades/readme.md)
* [ORM - Object relational mapping](/DAW/DAW-MP07/DAW-MP07-UF3/orm-object-relational-mapping/readme.md)
 
#### 1.2 S'han creat aplicacions que estableixin connexions amb bases de dades. 
#### 1.3 S'ha recuperat informació emmagatzemada en bases de dades.
#### 1.4 S'ha publicat en aplicacions web la informació recuperada. 
#### 1.5 S'han utilitzat conjunts de dades per emmagatzemar la informació.
#### 1.6 S'han creat aplicacions web que permetin l'actualització i l'eliminació d'informació disponible en una base de dades. 

**Accés a dades amb PHP**

* [PHP - Accés a dades amb PDO](/DAW/DAW-MP07/DAW-MP07-UF3/php-acces-a-dades-amb-pdo/readme.md)
* [PHP - Inserció de dades amb PDO](/DAW/DAW-MP07/DAW-MP07-UF3/php-insercio-de-dades-amb-pdo/readme.md)
* [PHP - Autenticació d'usuaris amb PDO - SQL Injection](/DAW/DAW-MP07/DAW-MP07-UF3/php-autenticacio-dusuaris-amb-pdo-sql-injection/readme.md)
* [PHP - MiniTwitter](/DAW/DAW-MP07/DAW-MP07-UF3/acces-a-dades-minitwitter/readme.md)

**Altres exercicis amb PHP**

* [SQL Injection amb my_sql](/DAW/DAW-MP07/DAW-MP07-UF3/sql-injecton-amb-my_sql/readme.md)

**Accés a dades amb l'ORM de Microsoft**

* [EF: Primera presa de contacte amb l'ORM de Microsoft.](/DAW/DAW-MP07/DAW-MP07-UF3/ef-primera-presa-de-contacte-amb-lorm-de-microsoft/readme.md)
* [ORM: exercicis crear models, insertar dades, consultar dades.](/DAW/DAW-MP07/DAW-MP07-UF3/django-exercicis-crear-models-insertar-dades-consultar-dades/readme.md)

**Accés a dades amb l'ORM de django**

* [django - Introducció als models](/DAW/DAW-MP07/DAW-MP07-UF3/django-introduccio-als-models/readme.md)
* [django - Definint models](/DAW/DAW-MP07/DAW-MP07-UF3/django-definint-models/readme.md)
* [django - Fent consultes sobre models](/DAW/DAW-MP07/DAW-MP07-UF3/django-fent-consultes-sobre-models/readme.md)

#### 1.7 S'han utilitzat transaccions per mantenir la consistència de la informació. 

**TX amb django**

* [django - Transaccions](/DAW/DAW-MP07/DAW-MP07-UF3/django-transaccions/readme.md)

**TX amb EntityFramework**


#### 1.8 S'han provat i documentat les aplicacions.

* [ORM, Pros and Cons](/DAW/DAW-MP07/DAW-MP07-UF3/orm-pros-and-cons/readme.md)


##Conceptes clau:

Un cop finalitzada aquesta UF que cal saber:

* Evitar SQL injection.
* Usar estructures d'iteració per recorrer el resultat d'una consulta.
* Integrar correctament les consultes al programa: no seleccionar tota una taula per després buscar una filera, cal demanar directament per aquella filera.
* Entendre els diferents tipus d'abstracció respecte la base de dades: des de les llibreries específiques d'una base de dades fins als ORM passant per llibreries que poden treballar amb divereses bases de dades. Avantatges i inconvenients de cada sistema.
* ORM: concepte d'ORM i avantatges.
* ORM: saber definir models i mapejar-los contra taules d'una base de dades relacional.
* ORM: concepte de migració i avantatges. Saber construir i aplicar migracions.
* ORM: Saber usar un ORM per a fer operacions CRUD bàsiques contra una base de dades.
* ORM: propietats de navegació: saber que són i saber explicar-ho. Avantatges de les propietats de navegació. Com mantenir el rendiment usant propietas de navegació. Bones pràctiques.

## Bibliografia:

Existeixen multitud de llenguatges de programació amb les seves corresponents eines d'accés a dades. Farem servir tres entorns de referència, no vol dir que siguin els millors, però algun s'ha de triar. Tots tres entorns tenen tota la documentació a Internet, manuals i tota una comunitat al seu voltant que crea contingut.

* PHP:
    * [Vendor specific database extensions](http://php.net/manual/en/refs.database.vendors.php)
    * [Database Extensions Abstraction Layer ](http://php.net/manual/en/refs.database.abstract.php)
* Microsoft [http://msdn.com/data/ef](entity framework) , en concret [code first / model first](https://msdn.microsoft.com/en-us/library/jj193542(v=vs.113).aspx)
* [django database abstraction api](https://docs.djangoproject.com/en/2.0/topics/db/queries/)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

---

###### Autor: daniel herrera 2016.10.25 12:57:27
###### Editat per: daniel herrera 2018.01.10 08:48:07
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
