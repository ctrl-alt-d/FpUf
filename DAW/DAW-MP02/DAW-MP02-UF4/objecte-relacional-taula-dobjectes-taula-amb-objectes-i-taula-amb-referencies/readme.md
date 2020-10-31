# Oracle Objecte-Relacional - Els prèstecs - Taula d'objectes, Taula amb Objectes i Taula amb referències
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Observa aquest DDL i DML escrit amb Oracle Objecte Relacional i respon a les preguntes finals:

Classe Dimensions:

```sql
create or replace type dimensions_typ as object (
    alcada float,
    amplada float,
    gruix float,
    member function volum return float
);
create or replace type body dimensions_typ as
  member function volum return float is
  begin
    return alcada * amplada * gruix;
  end;
end;
```


Taula de llibres: 

```sql
   CREATE TABLE "LLIBRE" 
   ("ISBN" VARCHAR2(11 BYTE) NOT NULL PRIMARY KEY, 
	"TITOL" VARCHAR2(100 BYTE), 
	"DIMENSIONS" "DIMENSIONS_TYP" 
   ) 
```

Inserto Llibre:

```sql
insert into llibre ( isbn, titol, dimensions ) values
( '111111', 'Harry Potter y el caliz de fuego', 
  dimensions_typ( 12.5, 11.3, 4.1   )
);

insert into llibre ( isbn, titol, dimensions ) values
( '222222', 'Harry Potter y la piedra filosofal', 
  dimensions_typ( 12.5, 11.3, 6.8   )
);
```

Creem la classe persona:

```sql
create or replace TYPE person_typ AS OBJECT (
  dni            VARCHAR2(20),
  nom            VARCHAR2(20),
  cognom         VARCHAR2(25),
  email          VARCHAR2(25),
  phone          VARCHAR2(20),
  MAP MEMBER FUNCTION get_dni RETURN varchar2
);

create or replace TYPE BODY person_typ AS
  MAP MEMBER FUNCTION get_dni RETURN varchar2 IS
  BEGIN
    RETURN dni;
  END;
END;

```
Creem la taula de socis:

```sql
create table socis of person_typ;
```

Insertem dos socis:

```sql
insert into socis values (
   person_typ( 'AAA', 'Daniel', 'H', 'dherrera@x.c', '1234' ) 
);	
insert into socis values (
   person_typ( 'BBB', 'Maria', 'I', 'miva@x.c', '1234' ) 
);
```

Creem la taula de prestecs:

```sql
create table prestecs (
    soci ref person_typ not null scope is socis,
    llibre varchar2(11) not null references llibre
);
```

Insertem dos prestecs:

```sql
declare
   persona ref person_typ;
begin
   select ref(p) into persona from socis p where p.dni = 'BBB';
   insert into prestecs values ( persona, '111111' );
end;	

insert into prestecs 
select  
    ref(p),
    '111111'
from socis p
where p.dni = 'AAA';
```

Fem select per conèixer el volum dels llibres prestats:

```sql
select 
   sum( ll.dimensions.volum() ) as TotalVolum,  
   sum( ll.dimensions.gruix )  as totalGruix
from llibre ll
inner join prestecs c
  on ll.isbn = c.llibre;	
```

**Preguntes**:

* Identifica quines taules són d'objectes, quines contenen objectes i quines tenen referències a objectes.
* Descriu l'univers de discurs d'aquesta base de dades.
* Comenta quins dos mètodes diferents s'han fet servir per insertar prèstecs.
* Identifica quines de les sentències no són DDL.
* Identifica on seleccionem propietats d'objectes i on invoquem mètodes d'objectes.





---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.C 1.F 1.G
* Continguts 1.1 1.3 1.4 1.8 1.9 1.10
---

###### Autor: daniel herrera 2014.04.02 17:32:01
###### Editat per: daniel herrera 2015.04.14 14:31:07
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
