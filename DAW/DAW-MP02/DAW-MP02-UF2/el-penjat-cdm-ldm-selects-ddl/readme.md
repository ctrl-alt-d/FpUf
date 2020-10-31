# El Penjat - CDM, LDM, Selects, DDL
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Observa aquestes sentències DDL i DML i contesta:

```sql
create table paraules (
  paraula varchar(100) not null,
  constraint paraules_pk
  primary key (paraula )
);

create table lletres (
  paraula varchar(100) not null,
  posicio int not null,
  lletra char(1) not null,
  constraint lletres_pk 
  primary key (paraula, posicio),
  constraint lletra_a_paraula_fk
  foreign key (paraula)
  references paraules (paraula )
  );


insert into paraules values
( 'Projector' ),
( 'Cotxe' ),
( 'Cortina' ),
( 'Impresora' );

insert into lletres values 
( 'Projector', 1, 'p'),
( 'Projector', 2, 'r'),
( 'Projector', 3, 'o'),
( 'Projector', 4, 'j'),
( 'Projector', 5, 'e'),
( 'Projector', 6, 'c'),
( 'Projector', 7, 't'),
( 'Projector', 8, 'o'),
( 'Projector', 9, 'r');

insert into lletres values 
( 'Cotxe', 1, 'c'),
( 'Cotxe', 2, 'o'),
( 'Cotxe', 3, 't'),
( 'Cotxe', 4, 'x'),
( 'Cotxe', 5, 'e');


create table estats (
  numero int not null,
  dibuix text not null,
  constraint estats_pk
  primary key ( numero )
  );

create table partides (
  id int not null ,
  jugador varchar(100) not null ,
  constraint partida_pk
  primary key (id)
);

create table LletresPartida (
   ordre int identity,          --MYSQL: auto_increment
   id_partida int not null,
   lletra char(1) not null,
   constraint lletresPartida_pk
   primary key ( ordre, id_partida ),
   constraint lletresPartides_a_partida_fk
   foreign key (id_partida)
   references partides ( id));


insert into estats values
( 1, 
'            
           
	          
	       
          
	          
	 
-----------------
' ),
( 2, 
'   -------
    |     
	|    
	|    
	|   
	|    
	|
-----------------
' ),
( 3, 
'   -------
    |     O
	|    /|\\
	|     |
	|    / \\
	|    |  |
	|
-----------------
' );


alter table partides add paraula varchar(100) not null;
alter table partides add constraint
   partides_a_paraula_fk 
   foreign key (paraula)
   references paraules (paraula);


insert into partides (id, jugador, paraula )
values ( 1, '1r DAW', 'projector' );

insert into LletresPartida (id_partida, lletra)
values (1, 'a' );

```

**Exercicis**

1. Fes el LDM a partir de les taules.
1. Fes el MCD a partir del LDM.
1. Escriu una select per saber quantes lletres estan encertades en una partida.
1. Escriu una select per saber quantes lletres estan malament en una partida.
1. Escriu una select per saber si un usuari ha guanyat una partida.


**Exemples de consultes*+




```sql
select count(  lp.lletra )
from lletresPartida lp
inner join partides p
   on lp.id_partida = p.id
inner join paraules para
   on para.paraula = p.paraula
inner join lletres ll
   on ll.paraula = p.paraula
      and ll.lletra = lp.lletra

-------------------

select count(  lp.lletra )
from lletresPartida lp
inner join partides p
   on lp.id_partida = p.id
inner join paraules para
   on para.paraula = p.paraula
left outer join lletres ll
   on ll.paraula = p.paraula
      and ll.lletra = lp.lletra
where ll.lletra is null;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2017.02.15 18:39:48
###### Editat per: daniel herrera 2017.02.20 19:28:28
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
