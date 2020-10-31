# T-SQL. Cursors al Zoo
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Observa aquest DDL i DML:

```sql
drop table animals;
drop table especies;

create table especies 
( codi int identity not null,
nom varchar(200) not null,
continent_origen varchar(200) not null,
constraint especies_pk primary key ( codi ),
constraint especies_uq1 unique ( nom ));

create table animals (
especie int not null,
num_xip int not null,
nom varchar(300) not null,
dia_neixement date not null,
data_baixa date null,
constraint animals_pk primary key ( num_xip ),
constraint animals_a_especie_fk foreign key (especie) references especies (codi));

insert into especies (nom, continent_origen) values
('impala','Africa' ),
('koala', 'Oceania'),
('canguro', 'Oceania'),
('cebra', 'Africa'),
('Tarantula', 'Africa' );

insert into animals values
(1, 1, '150cc', '2001-05-01', null),
(1, 2, '250cc', '2002-07-21', null),
(5, 3, 'Pelacuaia', '2012-07-2', null),
(5, 4, 'Peladuta', '2012-07-23', '2015-07-23');
```


Exercicis:

1. Fes un cursor que recorri totes les espècies i pinti el nom de cada espècie.
2. Dins el cursor anterior, fes un cursor que recorri tots els animals de cada espècie i pinti el nom de l'animal.

[Exemple de cursors imbricats de MS](https://msdn.microsoft.com/es-es/library/ms180169.aspx):

```sql
SET NOCOUNT ON;  
  
DECLARE @vendor_id int, @vendor_name nvarchar(50),  
    @message varchar(80), @product nvarchar(50);  
  
PRINT '-------- Vendor Products Report --------';  
  
DECLARE vendor_cursor CURSOR FOR   
SELECT VendorID, Name  
FROM Purchasing.Vendor  
WHERE PreferredVendorStatus = 1  
ORDER BY VendorID;  
  
OPEN vendor_cursor  
  
FETCH NEXT FROM vendor_cursor   
INTO @vendor_id, @vendor_name  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    PRINT ' '  
    SELECT @message = '----- Products From Vendor: ' +   
        @vendor_name  
  
    PRINT @message  
  
    -- Declare an inner cursor based     
    -- on vendor_id from the outer cursor.  
  
    DECLARE product_cursor CURSOR FOR   
    SELECT v.Name  
    FROM Purchasing.ProductVendor pv, Production.Product v  
    WHERE pv.ProductID = v.ProductID AND  
    pv.VendorID = @vendor_id  -- Variable value from the outer cursor  
  
    OPEN product_cursor  
    FETCH NEXT FROM product_cursor INTO @product  
  
    IF @@FETCH_STATUS <> 0   
        PRINT '         <<None>>'       
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
  
        SELECT @message = '         ' + @product  
        PRINT @message  
        FETCH NEXT FROM product_cursor INTO @product  
        END  
  
    CLOSE product_cursor  
    DEALLOCATE product_cursor  
        -- Get the next vendor.  
    FETCH NEXT FROM vendor_cursor   
    INTO @vendor_id, @vendor_name  
END   
CLOSE vendor_cursor;  
DEALLOCATE vendor_cursor;
```


**Solució**

```sql
declare @nom varchar(300), @id int;
declare @animal varchar(300);
declare especies_cur cursor for
   select e.codi, e.nom
   from especies e
   order by e.nom
open especies_cur;
fetch next from especies_cur into @id, @nom;
while @@FETCH_STATUS = 0 begin
   print 'Animals de l''especie: ' + @nom;

   --inner cursor
   declare animals_cur cursor for
      select a.nom
	  from animals a
	  where a.especie = @id;
   open animals_cur;
   fetch next from animals_cur into @animal;
   while @@FETCH_STATUS = 0 begin
       print '     ' + @animal;
       fetch next from animals_cur into @animal;
   end
   close animals_cur;
   deallocate animals_cur;
   --

   fetch next from especies_cur into @id, @nom;
end
close especies_cur;
deallocate especies_cur;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.05.10 16:38:43
###### Editat per: daniel herrera 2017.05.10 17:43:00
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
