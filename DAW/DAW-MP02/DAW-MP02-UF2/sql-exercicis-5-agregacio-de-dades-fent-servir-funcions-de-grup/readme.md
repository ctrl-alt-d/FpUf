# SQL Exercicis 5.1: Agregació de dades fent servir funcions de grup
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
A la base de dades [AdventureWorks (Ms-PL, Microsoft Public License)](https://msftdbprodsamples.codeplex.com/):


1) Les funcions de grup passen per moltes fileres per produir un resultat per grup. Cert o fals?

2) Tractament sistemàtic dels valors Nulls:

2.1) Quan hi ha un valor null en una agregació de grup el resultat és Null. Cert/Fals.

2.2) Les funcions de grup inclouen nulls als càlculs. Cert/Fals

3) La clàusula where restringeix les fileres abans de la seva inclusió al càlcul de grup. Cert/Fals.


4) Mostra el la quantitat de productes, preu més alt, el més baix, la suma i el preu mitjà de tots els productes amb preu superior a 0. Arrodoneix el resultat a les centenes.

5) Modifica la consulta anterior per mostrar la quantitat de productes, el preu més alt, el més baix (diferent de 0), la suma i el preu mitjà de tots els productes agrupats per categoria.


```sql
 select c."Name",
        count( * ) as productes,
        max( p.listprice ) as "preu màxim",
		min(p.listPrice ) as "preu mínim",
		sum(p.listPrice) as total,
		round( avg( p.listPrice),3 ) as "preu mitjà"
 from Production.product p 
 inner join Production.ProductSubcategory S
    on p.ProductSubcategoryID = s.ProductSubcategoryID
 inner join Production.ProductCategory C
    on c.ProductCategoryID = S.ProductCategoryID
 where p.listPrice > 0
 group by c.Name
```

6) Calcula quantes subcategories diferents tenen producte sense enumerar-les. Utilitza la clau forana de producte a subcategoria per a fer el recompte.

```sql
select count( distinct productsubcategoryId )
from Production.Product

```
7) Escriu una consulta per conèixer la diferència entre el preu més alt i el més baix.Tingues en compte només aquells productes amb preu superior a 100. Etiqueta la columna com a diferència.

8) Mostra el preu mig dels productes de cada categoria. No incloguis les categories amb un preu mig per producte inferior a 300. (Mira l'[ajuda clàusula having](https://youtu.be/SqfbEtfDXzA) ) Ordena de més petit a més gran.

```SQL
SELECT AVG( P.LISTPRICE) AS "Preu Mig", c.Name
FROM Production.Product p
INNER JOIN Production.ProductSubcategory s
   ON P.ProductSubcategoryID = S.ProductSubcategoryID
INNER JOIN Production.ProductCategory C
   ON C.ProductCategoryID = S.ProductCategoryID
GROUP BY c.Name
HAVING AVG(P.LISTPRICE) >= 300
ORDER BY  AVG( P.LISTPRICE) 
```


9) Mostra el número total de productes posat en venda cada any. Ordenat per any.


```sql
SELECT YEAR(p.SellStartDate) AS "ANY", COUNT( * ) AS "NUMERO DE PRODUCTES POSATS EN VENDA"
FROM Production.Product p
GROUP BY YEAR(p.SellStartDate)
ORDER BY YEAR(p.SellStartDate)
```

10) Mostra el número total de productes posat en venda cada categoria i any. Ordenat per categoria i any.

```sql
SELECT c.name as "Categoria",
       YEAR(p.SellStartDate) AS "ANY", 
       COUNT( * ) AS "NUMERO DE PRODUCTES POSATS EN VENDA"
FROM Production.Product p
INNER JOIN Production.ProductSubcategory s
   ON P.ProductSubcategoryID = S.ProductSubcategoryID
INNER JOIN Production.ProductCategory C
   ON C.ProductCategoryID = S.ProductCategoryID
GROUP BY YEAR(p.SellStartDate), c.name
ORDER BY c.name, YEAR(p.SellStartDate)
```


11) Mostra la quantitat mitjana de telèfons de contacte de tots treballadors. Inclús els que no tenen telèfons de contacte.

```sql
select p.FirstName, p.LastName, count(*)
from Person.Person p left outer join Person.PersonPhone t
   on p.BusinessEntityID = t.BusinessEntityID
group by p.FirstName, p.LastName
```


12) Crea una matriu on aparegui el nom de cada categoria i la quantitat de productes posats a la venda els anys 2011,2012 i 2013. Crea una columna per cada any amb el nom. Hauràs de fer servir el `case`.



```sql
SELECT c.name as "Categoria",
       count(  case when year(p.sellstartdate)=2005 then 1 else null end  )  AS "2005", 
       count(  case when year(p.sellstartdate)=2006 then 1 else null end  ) AS "2006", 
       count(  case when year(p.sellstartdate)=2007 then 1 else null end  ) AS "2007"
FROM Production.Product p
INNER JOIN Production.ProductSubcategory s
   ON P.ProductSubcategoryID = S.ProductSubcategoryID
INNER JOIN Production.ProductCategory C
   ON C.ProductCategoryID = S.ProductCategoryID
GROUP BY  c.name
ORDER BY c.name
```

Resultat exemple:

    Categoria	2005	2006	2007
    Accessories 3       7       19
    Bikes       30      23      44
    Clothing    7       16      12
    Components  32      39      61

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2016.12.14 17:31:37
###### Editat per: daniel herrera 2018.01.26 16:33:15
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
