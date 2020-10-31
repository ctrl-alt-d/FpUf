# SQL Exercicis 6: Subconsultes (solucions)
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
A la base de dades [AdventureWorks (Ms-PL, Microsoft Public License)](https://msftdbprodsamples.codeplex.com/):


1) Mostra els 10 primers productes (per ordre de data de posada en venta ) que es van posar a la venda després del darrer producte que es va posar a la venda el maig de 2012.

    
```SQL
select top 10 *
from Production.Product P2
where P2.SellStartDate >=
	(select min(p.SellStartDate)
	from Production.Product p
	where 
	    --year(p.SellStartDate)=2007 and month( p.SellStartDate ) > 5 
		p.SellStartDate >= '2007-06-01 00:00:00'
	)
order by P2.SellStartDate 

```
2) Mostra els 10 primers producte ( per ordre de preu ) per sobre del preu mig dels productes. Exclou al càlcul del preu mig els productes amb valor 0.

```sql
select top 10 p2.*
from production.product p2
where p2.ListPrice >
			(select avg( p.ListPrice )
			from production.product P
			where p.ListPrice <> 0)
order by p2.ListPrice

```
3) Mostra el codi de producte de tots els productes que el nom de la subcategoria contingui una 'k'. Cal resoldre-ho amb subconsulta.

```sql
select p.ProductId
from Production.Product P
where p.ProductSubcategoryID in
		( select s.ProductSubcategoryID
		from Production.ProductSubcategory s
		where s.Name like '%k%' )
```

4) Mostra els 10 primers codis de producte per ordre alfàbètic de subcategories de la categoria 'Bikes'. Plantaja la sentència mitjanant una subconsulta a subcategories.

```sql
--ull!! això ho resoldriem amb joins, ho fem amb subconsultes
--només per practicar.
select *
from Production.product P
where p.ProductSubcategoryID in
		(select S.ProductSubcategoryID
		from Production.ProductSubcategory S
		where S.ProductCategoryID =
					(select c.ProductCategoryID
					from production.ProductCategory C
					where C.Name = 'Bikes')
		)

```
6) Mostra les categories on hi hagi productes que costin més que el doble de la mitjana del preu de tots els productes amb preu superior a 100.


```sql
select distinct c.Name
from 
      production.ProductCategory C
inner join 
      Production.ProductSubcategory S
          on c.ProductCategoryID = s.ProductCategoryID
inner join 
      production.Product P
          on p.ProductSubcategoryID = S.ProductSubcategoryID
where p.ListPrice > (select 2* avg(p.ListPrice)
						from Production.product P
						where p.ListPrice > 100
					 )
```
7) Mostra les categories que no continguin productes que costin més de la meitat de la mitjana del preu de tots els productes amb preu superior a 100.


```sql
select distinct c.Name
from 
      production.ProductCategory C
inner join 
      Production.ProductSubcategory S
          on c.ProductCategoryID = s.ProductCategoryID
inner join 
      production.Product P
          on p.ProductSubcategoryID = S.ProductSubcategoryID
group by c.name
having max( p.ListPrice)  < (select  avg(p.ListPrice)/2
						from Production.product P
						where p.ListPrice > 100
					 )

```
8) Peprara una subquery on aparegui codi subcategoria i mitjana de preus dels productes d'aquella subcategoria. Fes un Join d'aquesta subquery amb les taules de productes, categories i subcategories. Ha d'apareixer el nom de la categoria, la subcategoria, el nom i preu de producte i la mitjana dels preus dels productes de la subcategoria.

```sql
select c.Name, s.Name, p.Name, SQ.mitjana_de_preu
from 
	( select s.ProductSubcategoryID, avg( p.listPrice ) as mitjana_de_preu
	from Production.ProductSubcategory s
	inner join Production.Product p
	 on p.ProductSubcategoryID = s.ProductSubcategoryID
	group by s.ProductSubcategoryID ) SQ
inner join Production.Product p
   on p.ProductSubcategoryID = SQ.ProductSubcategoryID
inner join Production.ProductSubcategory s
   on p.ProductSubcategoryID = s.ProductSubcategoryID
inner join Production.ProductCategory c
   on c.ProductCategoryID = s.ProductCategoryID

```
9) Investiga que és CTE i rescriu la consulta anterior fent servir CTE.

/*8) Peprara una subquery on aparegui codi subcategoria i mitjana de preus dels
 productes d'aquella subcategoria. 
 Fes un Join d'aquesta subquery amb les taules de productes, 
 categories i subcategories. Ha d'apareixer el nom de la categoria, 
 la subcategoria, el nom i preu de producte i la mitjana dels preus 
 dels productes de la subcategoria.
*/



```sql
with mitjana_preus as 
  ( select s.ProductSubcategoryID, avg( p.listPrice ) as mitjana_de_preu
	from Production.ProductSubcategory s
	inner join Production.Product p
	 on p.ProductSubcategoryID = s.ProductSubcategoryID
	group by s.ProductSubcategoryID )

select c.Name, s.Name, p.Name, SQ.mitjana_de_preu
from 
	 mitjana_preus SQ
inner join Production.Product p
   on p.ProductSubcategoryID = SQ.ProductSubcategoryID
inner join Production.ProductSubcategory s
   on p.ProductSubcategoryID = s.ProductSubcategoryID
inner join Production.ProductCategory c
   on c.ProductCategoryID = s.ProductCategoryID;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2018.02.02 14:08:33
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
