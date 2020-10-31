# Concepte i ús dels sistemes gestors de bases de dades
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Una **base de dades** és un conjunt endreçat d'informació que s'emmagatzema mitjançant algun tipus de suport i que es pot consultar i mantenir. Ex: recull de temperatures, padró d'habitants.

Un **sistema gestor de base de dades** és un programari `(*1)` especialitzat en la custòdia i manegament de dades `(*2)` tot oferint un mínim de prestacions `(*3)`.

* `(*1)` Pot ser una aplicació o unes llibreries. En cas de ser aplicació caldrà disposar d'un sistema de comunicació de processos per tal de poder-nos connectar. Existeixen diferents sistemes de comunicació: per pipes, per xarxa, per memòria compartida. En cas de ser llibreries caldrà enllaçar-les al nostre programa, ja sigui de manera estàtica en temps de compilació del programa o bé de manera dinàmica durant l'execució del mateix.

* `(*2)` Les aplicacions no accedeixen directament a les dades, li demanen al SGBD ( sistema gestor de base de dades) les operacions que volen realitzat. Exemple d'operacions poden ser modificació de dades o consulta de dades existents. El SGBD és qui realitza aquestes operacions mantenint la integritat de les dades i aplicant la seguretat que estigui definida al sistema.

* `(*3)` Per tal que un programari pugui considerar-se SGBD ha de ser capaç de facilitar una sèrie d'operacions mínimes des de diferents vesants, una de les capacitats més importants que ha de tenir és la independència de les dades respecte les aplicacions ( podem seguir accedint a les dades mitjançant les utilitats del SGBD sense necessitat d'altres aplicacions, podem canviar l'estructura de les dades des del propi SGBD). Altres capacitats poden ser facilitar l'accés a les dades i mantenir la seguretat i integritat de les mateixes.

![SGBD](http://i.imgur.com/qFuNOo6.png)

### Exercicis###

1. StackOverflow és una web de referència al món del desenvolupament de programari. Consulta quantes preguntes hi ha en total a la web stackoverflow.com. 
2. Consulta la defininció que trobem a StackOverflow per els següents Tags, comprova també quantes consultes hi ha per cadascun d'ells: Oracle, SQL-Server, MYSQL, postgresql, MongoDB, Cassandra, ms-access, sqlite. Per cadascun d'ells busca altres tags relacionats.
2. Stackoverflow emmagatzema les preguntes i respostes un una base de dades sql-server. Es poden realitzar consultes via web a aquesta base de dades. Observa la consulta: https://data.stackexchange.com/stackoverflow/query/483836/database-ranking . Amb el resultat fes una taula on es vegi quin % de les preguntes d'stackoverflow són relatives a cadascun d'aquests tags tant als darrers dos anys com des de l'inici del servei. Utilitza el resultat de la consulta i un full de càlcul.
4. Existeixen definicions molt més formals del que és un SGBD. Busca alguna d'aquestes definicions en anglès i tradueix-la al teu idioma. Busca per 'Database Management System'.
5. El sistema gestor de base de dades pot ser un procés que s'executa a la màquina ( ex: Oracle, SQL Server, MYSQL ) o bé poden ser unes llibreries, unes dll en el cas Windows ( ex: Access, sqlite ). Observa aquestes captures del gestor de tasques i digues a quin SGBD creus que es corresponen.

![Oracle](http://i.imgur.com/CbtJX2J.png)

![SQL Server](http://i.imgur.com/xGf5SUi.png)



>
>######Aquest exercici està extret del llibre [Introducció a les Bases de Dades](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>



######[Exemple de solució](https://drive.google.com/file/d/0B-mGiOFcUtNyM0JJbjBZWGJIa1U/view?usp=sharing)

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.05.09 07:29:29
###### Editat per: daniel herrera 2016.09.20 16:40:08
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
