# Oracle Objecte-Relacional - Els actors - Taula d'objectes amb mètode i taula amb columna referència a objecte
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
**Objectiu didàctic**

 * Treballar amb taules d'objectes.
 * Treballar amb taula de referència a objectes.
 * Invocar mètodes de l'objecte.

**DDL** Creació del tipus objecte i del seu mètode

```SQL
--Creació del tipus
Create or Replace type Actor As Object (
  Nom                 varchar2(20),
  Nacionalitat        varchar2(30),
  DataNaixament        date,
  Member Function Edat return integer
);

--Creem la funció
Create or replace type body Actor As
  Member Function Edat return integer is
           Any_actual integer;
           Any_naixament integer;
        Begin 
           Select Extract(Year from Sysdate) into Any_actual from dual;
           Select to_number(to_char(DataNaixament,'YYYY')) into Any_naixament from dual;
           return Any_actual - Any_naixament;
        End;
End;
```

**DDL** Creació de taula d'objectes i taula que conté referència a objecte.

```SQL
--Creem la taula Actors
Create table Actors Of Actor;

--Creem la taula pel·licula que tindra la referencia a Actors
create table Peli (
  Nom               varchar2(30),
  DataEstrena   date,
  Protagonista Ref Actor Scope Is Actors
);

```

**DML** inserció de dades a la taula d'objectes:

```SQL
--Insert Actors
insert into Actors Values (
   Actor ('Bruce Willis','Americana','02/02/1963'));
insert into Actors Values (
   Actor  ('Arnold','Austriac','08/10/1948') );
insert into Actors Values (
  Actor  ('DiCaprio','Italiano','10/12/1976') );
```

**DML** inserció de dades a la taula que referencia objectes mitjançant una variable:

```SQL
--Afegim una Peli d un actor
declare
  dades_peli ref Actor;
begin
  Select Ref(a) into dades_peli from Actors a where a.Nom = 'Arnold';
  Insert into Peli (Nom,DataEstrena,Protagonista)
        Values ('Terminator2','02/08/1980',dades_peli);
end;

```
**DML** invocació d'un mètode de l'objecte:

```SQL
--Seleccionem l'edat del actor Arnold
select a.Edat() from Actors a where a.Nom = 'Arnold';

```
**Exercicis**

Executa aquestes sentències al teu entorn Oracle tot comprovant i entenent els resultats.

*By D.López & R.Saulis & A.Ramírez (DAW'2014)*


---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.C 1.F 1.G
* Continguts 1.1 1.3 1.4 1.6 1.8 1.9 1.10
---

###### Autor: daniel herrera 2014.04.11 14:14:39
###### Editat per: daniel herrera 2014.04.11 15:31:58
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
