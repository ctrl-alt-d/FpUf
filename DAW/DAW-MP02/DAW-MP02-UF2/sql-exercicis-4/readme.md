# SQL Exercicis 4: Visualització de dades de vàries taules
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
A la base de dades [AdventureWorks (Ms-PL, Microsoft Public License)](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks):

* [Introducció exercici Visualització de dades de Vàries taules](https://youtu.be/yAVgreAOC4Y) YT 31'

1) Escriu una consulta per mostrar el correu de la persona que fa el review, el nom del producte ( `[Production].[Product]` ) i el rating per a tots els reviews ( `[Production].[ProductReview]`) amb rating de 5 estrelles i que l'adreça de correu comenci per l.

2) Crea un llistat únic de tots els productes de la categoria 'Bikes'. Inclou a la consulta el nom de la categoria i la subcategoria.

```sql
select top 100
   c.name, s.name, p.Name
from
   [Production].[Product] p
inner join 
   [Production].[ProductSubcategory] s
   on p.ProductSubcategoryID = s.ProductSubcategoryID
inner join
   [Production].[ProductCategory] c
   on c.ProductCategoryID = s.ProductCategoryID
where
   c.name = 'Bikes'
```

3.1) Selecciona el nom de la persona (nom i cognom ) amb els seus números de telèfon ( t'apareixerà un telèfon per filera, és ok ). Nota: has de fer join de *persones* amb *telèfons* mitjançant el camp `BusinessEntityID`

3.2) Selecciona el nom de la persona (nom i cognom ) amb les seves adreces de correu electrònic. Nota: has de fer join de *persones* amb *emails* mitjançant el camp `BusinessEntityID`

3.3) Modifica 3.1 per tal que aparegui, a més, el tipus de telèfon `PhoneNumberType`. Nota: has de fer el join de *telèfons* amb *tipus de telèfon* mitjançant el camp `PhoneNumberTypeID`
 
3) Els telefons de contacte de tipus 'Feina' (`[Person].[PhoneNumberType]`) de les persones ( `[Person].[Person]` ) amb un email ( `[Person].[EmailAddress]` ) que comenci per 'e'. Mostrar nom de la persona i cognom i número de telèfon. No posar repetits. Nota: has de fer join de *persones* amb *emails* (mitjançant `BusinessEntityID`), *persones* amb *telèfons* (mitjançant `BusinessEntityID`) i *telèfons* amb *tipus de telèfon* (mitjançant `PhoneNumberTypeID`):

```sql
select distinct 
       P.FirstName, p.LastName, F.PhoneNumber
from
   [Person].[Person] P
inner join [Person].[EmailAddress] E
   on P.BusinessEntityID = E.BusinessEntityID
inner join [Person].[PersonPhone] F
   on F.BusinessEntityID = P.BusinessEntityID
inner join [Person].[PhoneNumberType] NT
   on F.PhoneNumberTypeID = NT.PhoneNumberTypeID
WHERE E.EmailAddress like 'e%'
      and NT.Name = 'Work'
```

4) El nom i cognom de les 10 persones `.[Person].[Person]` que han canviat el password `.[Person].[Password]` més recentment. Fes el join amb `[BusinessEntityID]`

5) Entre producte i foto del producte hi ha una relació N:M. **Primera part**: Fes una consulta per averiguar quan és va fer la darrera sessió de fotos ( ordenant les fotos per la data de manera descendent ) Apunta la data en un paper. **Segona part**: Ara fés una nova consulta per mostrar els productes que apareixen a les fotos que es van fer a la data trobada a la primera part. **Nota**: Al ser una interrelació N:M entre foto i producte, has de trobar una tercera taula que contindrà FKs a les dues taules esmentades.

6) Crea una consulta per mostrar els productes que es van posar a la venda després del producte amb codi 'WB-H098'

7) **Bonus point** Totes les persones que han coincidit amb Laura Norman en algun departament, cal posar les dates en que va treballar Laura, les dates en que va treballar l'altre persona i el nom de departament.

**Exemple de consulta**

Treballadors acompanyats del departament on estan treballant actualment, ordenat per depatament i dins de departament per nom del treballador:


```sql
select p.FirstName, d.Name
from [HumanResources].[Department] D
inner join [HumanResources].[EmployeeDepartmentHistory] h
  on d.DepartmentID = h.[DepartmentID] 
inner join [HumanResources].[Employee] e
  on e.[BusinessEntityID] = h.[BusinessEntityID]
inner join [Person].[Person] p
  on e.[BusinessEntityID] = p.[BusinessEntityID]
where
  h.EndDate is null
order by
  d.Name, p.FirstName 
```

**Outer joins**

a. Modifica l'exercici 1 per tal que apareguin totes les categories encara que no tinguin subcategoria o producte.

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2016.12.07 17:46:17
###### Editat per: daniel herrera 2018.08.24 17:34:10
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
