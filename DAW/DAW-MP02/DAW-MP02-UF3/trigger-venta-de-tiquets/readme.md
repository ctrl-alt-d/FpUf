# Trigger. Venta de tiquets.
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Una web especialitzada en la venta d'entrades es troba amb problemes perquè de vegades es venen més estrades de les que realment es poden posar a la venta. L'estructura de dades és:

* `Esdeveniment`: codi (pk), nom, n_entredes_a_la_venta, n_entrades_venudes (default 0).
* `Entrada`: codi (pk), dni_comprador, esdeveniment (fk )

Escriu un trigger que actualitzi n_entrades_venudes i que no permeti vendre més entrades de n_entredes_a_la_venta. Nota: el camp n_entrades_a_la_venta no cal tocar-lo mai.


```sql
create table esdeveniment
(codi int not null,
 nom varchar(500) not null,
 n_entrades_a_la_venda int not null,
 n_entrades_venudes int not null default 0,
 constraint esdeveniment_pk
 primary key ( codi ));

insert into esdeveniment 
(codi, nom, n_entrades_a_la_venda)
values
(1,'Barça madrid', 5 ),
(2,'Concet Madonna', 9 ),
(3,'Màgia amb Juan tamariz', 1000 );

create table entrada 
( codi int identity not null,
  dni_comprador varchar(200) not null,
  esdeveniment_codi int not null,
  constraint entrada_pk primary key (codi),
  constraint entrada_a_esdeveniment_fk
  foreign key ( esdeveniment_codi )
  references esdeveniment ( codi ));

go
create trigger entrades_insert_check
on entrada after insert
as begin
   --- actualitzo el comptador d'entrades venudes
   update e
   set e.n_entrades_venudes = e.n_entrades_venudes + i.QTAT
   from esdeveniment e
   inner join 
     ( select i.esdeveniment_codi, count(*) as QTAT
	   from inserted i
	   group by i.esdeveniment_codi ) i
      on i.esdeveniment_codi = e.codi;
    
	--- control de entrades venudes
	if exists( select * 
	           from esdeveniment   
	           where n_entrades_venudes > n_entrades_a_la_venda ) begin
		RAISERROR ('oh! T''has passat!', 16, 1);  
		ROLLBACK TRANSACTION; 
	end
end;

insert into entrada values
( 'sdfsafsa', 1 ),
( 'ereww', 1 ),
( 'eerere', 1 ),
( 'sdfsafsa', 1 );

go
create trigger entrades_delete_allow
on entrada after delete
as begin
   --- actualitzo el comptador d'entrades venudes
   update e
   set e.n_entrades_venudes = e.n_entrades_venudes - i.QTAT
   from esdeveniment e
   inner join 
     ( select i.esdeveniment_codi, count(*) as QTAT
	   from deleted i
	   group by i.esdeveniment_codi ) i
      on i.esdeveniment_codi = e.codi;
    
end;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2017.04.25 14:22:01
###### Editat per: daniel herrera 2017.04.25 17:25:17
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
