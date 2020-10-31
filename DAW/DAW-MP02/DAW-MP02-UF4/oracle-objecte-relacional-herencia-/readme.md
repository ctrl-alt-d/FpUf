# Oracle Objecte-Relacional - Herència - Els Muggles
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Crea les classes:

* PoderMàgic_typ( nom, força, destreça, intel·ligència )
* PodersMàgics_typ com a taula de poders màgics.

Crea aquesta jerarquia de classes:

* Persona ( NIF, nom, dataNeixement, mètode: edat )
    * Muggle ( nacionalitat )
    * PureBlood ( podersMagics, mètodes: nomPoders, totalForça, totalDestreça, totalIntel·ligència)

La classe Persona és no instanciable.

Crea la taula `persones` com a taula d'objectes de tipus `Persona`.
Inserta 3 Muggles i 3 PureBloods.
Selecciona:
    * El nom de totes les persones.
    * El total de força de tots els PureBloods.

Recorda:

>You can find the typeid of a specified object instance using the function [SYS_TYPEID](http://docs.oracle.com/cd/E11882_01/appdev.112/e11822/adobjbas.htm#ADOBJ7161)

    SELECT NIF, SYS_TYPEID(VALUE(p)) typeid 
      FROM persones p;

>The catalog views USER_TYPES, DBA_TYPES, and ALL_TYPES contain a TYPEID column (not hidden) that gives the typeid value for each type. You can join on this column to get the type names corresponding to the typeids in a type-discriminant column.

Has d'usar la funció TREAT per tractar una persona com a Muggle o PureBlood:

    SELECT NIF, TREAT(VALUE(p) AS Muggle)
      FROM persones p;
 





---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2015.04.21 15:01:23
###### Editat per: daniel herrera 2015.04.21 15:35:53
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
