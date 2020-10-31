# Funcions. Preu de producte a una data
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Primera part
=============


Crea dues taules a la base de dades relacionades entre si. La taula `productes` i la taula `històricPreusProductes`.

* La taula `productes` tindrà el codi i nom dels productes.
* La taula `històricPreusProductes` tindrà la clau forana a producte ( que formarà part de la pk), la data entrada en vigor del preu ( que també formarà part de la pk) i la data de finalització d'aquell preu ( que pot ser null si encara està en vigor ) i el preu (que no pot ser null).

Crea ara una funció que donat un codi de producte i una data ens digui quin preu tenia el producte en aquella data.



```sql
go
create table productes(
   codi int identity not null,
   nom varchar(200) not null,
   constraint producte_pk
   primary key ( codi ),
   constraint producte_nom_uk
   unique (nom)
);
go
insert into productes values
( 'bicicleta' ),
( 'poma' ),
( 'cadira' );
go
select * from productes;
go
create table historicPreus (
   codi int not null,
   data_inici date not null ,
   data_fi date null,
   preu money not null,
   constraint historicpreus_pk
   primary key (codi, data_inici ),
   constraint historicpreus_producte_fk
   foreign key (codi)
   references productes (codi)
   )
go
insert into historicPreus values
(  4, '2001-01-01', '2004-06-01', 400 ),
(  4, '2004-06-02', null, 440 ),
(  5, '2001-10-01', '2004-12-01', 500 ),
(  5, '2004-12-02', null, 550 );

go
create function get_preu( @codi int, @data date)
returns money
as begin
     declare @preu money;

	 select @preu = preu
	 from historicPreus h
	 where h.codi = @codi and
	       --((@data between h.data_inici and h.data_fi)
		    --or 
			--(h.data_inici < @data and h.data_fi is null)
			--)
			(@data between h.data_inici and coalesce(h.data_fi,getdate()))
	 return @preu;
end

go
select dbo.get_preu( 5, '2002-01-01' )
```

Segona Part
===========

Suposem que tenim `factures`, `línies de factura` i `compres`. Fes una funció per tal que digui quin és l'stock exacte d'un producte a data d'avuí.

**solució**

```sql
--creem la taula de factures
create table factures (
data_factura date not null,
data_entrega date not null,
numero_factura int identity not null,
descripcio varchar(400) not null );

alter table factures add constraint 
factures_pk primary key (numero_factura);

--insertem unes factures
insert into factures values 
( '2017-03-27',  '2017-03-29', 'Factura XXX'), 
( '2017-03-15',  '2017-03-16', 'Factura YYY');

--creem la taula de línies de factura
create table liniesDeFactura (
   numero_factura int not null,
   codi_producte int not null,
   qtat int not null,
   constraint linies_a_factures_fk
   foreign key ( numero_factura )
   references factures ( numero_factura ),
   constraint linies_a_productes_fk
   foreign key (codi_producte)
   references productes (codi),
   constraint linies_pk
   primary key ( numero_factura, codi_producte )
   );

--insertem unes línies de factura
insert into liniesDeFactura values 
( 1, 4, 100 ),
( 1, 5, 500 ),
( 2, 4, 300 ),
( 2, 5, 3500 );

-creem la taula de compres
create table compres (
   data_compra date not null,
   data_entrega date null,
   codi_producte int not null,
   qtat int not null,
   codi_ordre_de_compra int identity not null,
   constraint compres_pk
   primary key (codi_ordre_de_compra),
   constraint compres_a_producte_fk
   foreign key ( codi_producte )
   references productes ( codi )); 

--insertem unes quantes compres
insert into compres values
( '2017-1-1','2017-1-2', 4, 150 ),
( '2017-1-1','2017-1-2', 5, 100 ),
( '2017-2-1','2017-2-2', 5, 500 );

--creem la funció
go
create function dbo.get_stock( @codi_producte int )
returns int
as begin
   declare @total_compres int;
   declare @total_ventes int;

   select @total_compres = coalesce(sum( c.qtat ),0)
   from compres c
   where c.codi_producte = @codi_producte
     and c.data_entrega <= getdate()

   select @total_ventes = coalesce(sum(lf.qtat),0)
   from liniesDeFactura lf 
   inner join factures f
   on lf.numero_factura = f.numero_factura
   where lf.codi_producte = @codi_producte
   and f.data_entrega <= getdate()

   return @total_compres - @total_ventes;
end;

--probem la funció
select *, dbo.get_stock(p.codi) from productes p
```



Tercera part
=============

Crea un procediment emmagatzemat que fixi nous preus per als productes. Tingues en compte que només es poden canviar preus del futur i que cal actualitzar la `data_fi` del preu actual.

**Solució**

```sql
create procedure nou_preu @codi_producte int, 
                          @des_de date,
						  @preu money
as begin
   --1
   if @des_de <= cast( getdate() as date ) begin
      return -1;
   end;   
   --iniciem la transacció
   begin transaction tx1;
   set transaction isolation level serializable;
   --2 (esborro qualsevol altre preu del futur)
   delete from historicPreus
    where data_inici >= @des_de;
   --3.1 ( anoto la filera a actualitzar )
   declare @data_inici_preu_anterior date;
   select top 1 @data_inici_preu_anterior = h.data_inici
   from historicPreus h
   where h.codi = @codi_producte 
   order by h.data_inici desc;
   --3.2 (actualitzo data fi)
   update historicPreus
     set data_fi = DATEADD( day, -1, @des_de )
	where codi = @codi_producte and 
	      data_inici = @data_inici_preu_anterior;
   --4
   insert into historicPreus values
   ( @codi_producte, @des_de, null, @preu );
   --fi
   commit;
end;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.03.22 17:37:02
###### Editat per: daniel herrera 2017.03.28 17:50:56
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
