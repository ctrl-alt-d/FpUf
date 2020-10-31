# SQL Exercicis 3: Funcions d'una sola filera
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Pràctica 3: Funcions d'una sola filera

A la base de dades [AdventureWorks (Ms-PL, Microsoft Public License)](https://msftdbprodsamples.codeplex.com/):

[Xuleta de funcions T-SQL](https://docs.microsoft.com/en-us/sql/t-sql/functions/functions)

1. Escriu una consulta per mostrar la data actual. Etiqueta la columna com 'Data'

2. Per a cada producte, mostra el codi de producte, el nom, el preu i el preu amb un aument del 15% expressat com un número enter sense decimals. Etiqueta'l com a 'Nou preu'

3. Modifica la consulta anterior per afegir una columna que resti el preu antic del nou. Etiqueta com a 'Increment'.

4. Escriu una consulta que mostre el nom del producte amb totes les lletres en majúscules així com la llargada del nom de producte per aquells productes que comencin per vocal. Ordena el resultat per longitud del nom del producte, primer el més llarg. Per comprovar si comença per volca utilitza a la condició `SUBSTRING( Name,1,1) IN (...`.

5. Per a cada producte mostra el nom així com el número de mesos que ha estat en venta i el número de mesos que fa que es va posar en venta per primer cop. Etiqueta com 'Mesos en venta', 'Mesos inici venta'. Arrodoneix els mesos.

6. Escriu una consulta que produeixi el següent. Per a cada producte: `Nom de producte` val `Preu` però hauria de valdre `Preu*3`.

7. Creaa una consulta per mostrar el nom i preu de tots els productes. Formateja el preu per a que tingui 15 caracters, omplit l'esquerra amb 0. Etiqueta com a 'Preu'. Utilitza la tècnica d'en [Patrick](http://stackoverflow.com/a/5540118/842935) tot entenent cada funció que facis servir.

8. Mostra el nom del producte, el preu i el dia de la setmana que es va posar a la venta. Etiqueta la darrara columne com `dia`. Ordena els resultats per dia de la setmana.

9. Mostra tots els productes i la seva class, si un producte no té class llavors has de mostrar `No class`. (Feu servir [COALESCE](https://docs.microsoft.com/en-us/sql/t-sql/language-elements/coalesce-transact-sql), també podeu ser servir [IFNULL](https://docs.microsoft.com/en-us/sql/t-sql/functions/isnull-transact-sql) )

10. Crea una consulta que mostri el nom del producte i el preu amb asteriscs. Cal que mostri un asterisc per cada 100$. Pots fer servir la funció [replicate](https://msdn.microsoft.com/en-us/library/ms174383.aspx).

11. Utilitzant un case decodifica el camp id subcategoria segons aquesta taula:

Taula: 

    SubcategoryID      Name
    1                  Mountain Bikes
    2                  Road Bikes
    3                  Touring Bikes
    4                  Handlebars
    Altres --->        Other

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2016.12.05 18:23:07
###### Editat per: daniel herrera 2018.01.11 17:52:01
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
