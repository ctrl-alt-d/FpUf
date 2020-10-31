# Oracle Objecte-Relacional - Els mariners - Col·leccions
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Crea un objecte anomenat `mariner_typ` amb els atributs `dni`, `nom`, `rang`.

Crea la taula `vaixells` amb els atributs `matricula`, `nom`, `tripulació`. La tripulació l'has de definir com una col·lecció de mariners (no oblidis crear el tipus `tripulacio_typ`).

Inserta dos vaixells amb les seves tripulacions, enrecorda't-en de crear un capità a la tripulació.

Selecciona el capità del primer vaixell que has creat.

Inserta 1000 mariners a un vaixell de la base de dades on ja hi hagi tripulació.

Modifica alguna de les dades contingudes a les col·leccions.

Pots ajudar-te amb la documentació d'[Oracle: Performing DML Operations on Collections](https://docs.oracle.com/database/121/ADOBJ/adobjcol.htm#ADOBJ7271)

**Ajuda**

Creació del tipus mariner:

```sql
CREATE TYPE mariner_typ AS OBJECT(
  dni varchar2(10),
  nom varchar2(40),
  rang varchar2(40));
  
```
Creació de la col·lecció:

```sql
CREATE TYPE tripulacio_typ AS TABLE OF mariner_typ;
```

Creació de la taula vaixells:
    
```sql
CREATE TABLE vaixells(
  matricula varchar2(10) PRIMARY KEY,
  nom varchar2(40),
  tripulacio tripulacio_typ)
  NESTED TABLE tripulacio STORE AS tripulacio_nt;
  
```
Inserció dels dos vaixells:

```sql
insert into vaixells
values('1234',
        'prova1',
        tripulacio_typ(mariner_typ('001','pere','capita'),
                        mariner_typ('002','pere2','groumet'),
                        mariner_typ('003','pere3','groumet')));
```

    insert into vaixells
    values('12344',
            'prova2',
            tripulacio_typ(mariner_typ('001','pere','capita'),
                            mariner_typ('002','pere2','groumet'),
                            mariner_typ('003','pere3','groumet')));

Selecció del capità del vaixell amb una select:

```sql
select v.matricula, v.nom, t.nom ,  t.*
    from vaixells v, table(v.tripulacio) t
    where t.rang = 'capita' and v.nom='prova1';
    
    
```
Selecció del capità del vaixell iterant sobre la col·leció:

```sql
set serveroutput on
DECLARE
  i INTEGER;
  tripulacio tripulacio_typ;
  capita mariner_typ;
  j INTEGER;
BEGIN
  SELECT v.tripulacio INTO tripulacio FROM vaixells v WHERE v.nom = 'prova1';
  FOR i IN 1..tripulacio.COUNT LOOP
    IF (tripulacio(i).rang = 'capita')
      THEN
        DBMS_OUTPUT.PUT_LINE(tripulacio(i).nom);
    END IF;
  END LOOP;
END;
```

Insertar 1000 mariners en un vaixell que ja hi és a la base de dades:

```sql
declare 
   i integer;
begin
  i := 1;
  while (i < 1001) loop
    insert into 
    table( select v.tripulacio  FROM vaixells v WHERE v.nom = 'prova1')
    select mariner_typ(to_char(i),'N' || to_char(i) , 'netejador') from dual;
  i := i + 1;
  end loop;
end;
```


    

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.E 1.F 1.6
* Continguts 1.1 1.3 1.4 1.7 1.8 1.9 1.10
---

###### Autor: daniel herrera 2014.04.04 13:29:26
###### Editat per: daniel herrera 2016.04.11 14:37:12
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
