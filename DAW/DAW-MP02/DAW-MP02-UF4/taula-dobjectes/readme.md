# Oracle Objecte-Relacional - Els animals - Taula d'objectes
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Crea l'objecte **Animal** i la taula d'objectes **Animals**.

Un animal té les següents propietats:

* Nom
* Número de Potes
* Alçada
* Fressa

I els següents mètodes

* Parla  ( que per ara retorna per consola el contingut de Fressa )

Inserta 4 animals a la taula d'animals: Gallina, Conill, Velociraptor, Unicorn.

Crea la taula **Zoo**. Aquesta taula contindrà els següents camps:

* Chip ( clau primària )
* Referència a animal
* Data entrada al zoo
* Data defunció ( pot ser null )

Inserta la Gallina amb número de Chip '343242454' i el Velociraptor amb número de Chip '9695844'.

Escriu un tall de codi per a fer parlar el Velociraptor.

**Ajuda per a fer l'exercici**

```SQL
--CREACIÓ DEL TIPUS ANIMAL:
CREATE TYPE animal AS OBJECT (
    nom VARCHAR(20),
    potes NUMBER,
    alsada NUMBER(5,2),
    fressa VARCHAR(40),
    MEMBER FUNCTION parla RETURN VARCHAR2);
/
CREATE OR REPLACE TYPE BODY animal AS
    MEMBER FUNCTION parla RETURN VARCHAR2 IS
    BEGIN
        RETURN fressa;
    END;
END;
/

--Crear taula d’animals:
CREATE TABLE animals OF animal;

--Inserir animals:
INSERT INTO animals VALUES(
  animal('Gallina', 2, 26.9, 'COCOCOCOC'));
INSERT INTO animals VALUES(
  animal('Conill', 4, 24.7, 'CRCRCRCR'));
INSERT INTO animals VALUES(
  animal('Velociraptor', 4, 316.1, 'TEKTEKTEKT'));
INSERT INTO animals VALUES(
  animal('Unicorn', 4, 145.9, 'BBBRRRR'));

--Crear taula zoo:
CREATE TABLE zoo (
  chip NUMBER PRIMARY KEY,
  animal REF animal,
  dataEntrada DATE,
  dataDefuncio DATE NULL);

--Inserir la gallina al zoo:
DECLARE
  anim REF animal;
BEGIN
  SELECT REF(p) INTO anim FROM animals p WHERE p.nom = 'Gallina';
  INSERT INTO zoo VALUES (
    343242454, anim, '24 Jun 1998', NULL);
END;

--Inserir el Velociraptor al zoo:
DECLARE
  anim REF animal;
BEGIN
  SELECT REF(p) INTO anim FROM animals p WHERE p.nom = 'Velociraptor';
  INSERT INTO zoo VALUES (
    9695844, anim, '24 Jun 2003', NULL);
END;

--Fer cridar el Velociraptor:
set serveroutput on;
exec DBMS_OUTPUT.ENABLE;
DECLARE
  anim animal;
BEGIN
  SELECT value(p) INTO anim FROM animals p WHERE p.nom = 'Velociraptor';
  --SELECT deref(ref(p)) INTO anim FROM animals p WHERE p.nom = 'Velociraptor';
  DBMS_OUTPUT.PUT_LINE(anim.parla());
END;
```

    --des del zoo:
    DECLARE
      anim animal;
    BEGIN
      SELECT deref(z.animal) INTO anim 
      FROM zoo z WHERE z.animal.nom = 'Velociraptor';
      DBMS_OUTPUT.PUT_LINE(anim.parla());
    END;

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

* Resultats d'aprenentatge 1.B 1.C 1.F 1.G
* Continguts 1.1 1.3 1.4 1.8 1.9 1.10
---

###### Autor: daniel herrera 2014.03.31 17:08:49
###### Editat per: daniel herrera 2018.04.10 13:01:14
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
