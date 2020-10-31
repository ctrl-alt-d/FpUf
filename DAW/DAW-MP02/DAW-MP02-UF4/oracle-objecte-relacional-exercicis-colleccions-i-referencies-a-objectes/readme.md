# Oracle Objecte-Relacional - Exercicis col·leccions i referencies a objectes.
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Exercici 1
==========

Oracle diu que quan crees un camp de tipus referència a una taula *pots* especificar, mitjançant la paraula reservada SCOPE, a quina taula s'emmagatzema aquell objecte, per tal de restringir l'àmbit d'objectes a referenciar. Comprova:

* Que realment es tracta d'una opció i no una obligació.
* Que realment restringeix i no et deixa referenciar un objecte que estigui en una altre taula.


Exercici 2
==========

Quan creem taules amb objectes que contenen col·leccions d'objectes ( com a taula d'objectes ) Oracle ens proposa que creem la 'storage' table per si volem crear indexos:


```sql
CREATE TABLE students (
   graduation DATE, 
   math_majors people_typ, -- nested tables (empty)
   chem_majors people_typ, 
   physics_majors people_typ)
  NESTED TABLE math_majors STORE AS math_majors_nt  -- storage tables
  NESTED TABLE chem_majors STORE AS chem_majors_nt
  NESTED TABLE physics_majors STORE AS physics_majors_nt;

CREATE INDEX math_idno_idx ON math_majors_nt(idno);
CREATE INDEX chem_idno_idx ON chem_majors_nt(idno);
CREATE INDEX physics_idno_idx ON physics_majors_nt(idno);

```
Comprova si és obligatori o no crear la 'storage' table o bé és opcional.

Exercici 3
==========

Podem pensar les referències a objectes com una clau forana a un objecte. Però oracle ens diu que no gestina la integritat referencial:

>*Dangling REFs*

>It is possible for the object identified by a REF to become unavailable through either deletion of the object or a revoking of privileges. Such a REF is called dangling. Oracle SQL provides a predicate (called IS DANGLING) to allow testing REFs for this condition.

Comprova que pots esborrar objectes referenciats i el funcionament de l' `IS DANGLING`.

Entregables
===========

Cal entregar un pdf amb el plantejament de com faràs les comprovacions i captura de pantalla de les comprovacions on es vegin els resultats de les mateixes. Conculsions si s'escau.




---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2016.04.11 14:56:04
###### Editat per: daniel herrera 2016.04.11 15:43:57
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
