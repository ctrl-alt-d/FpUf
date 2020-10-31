# El concepte de dependències funcionals i els seus tipus.
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Tot el procés de normalització té un fonament matemàtic i les definicions es poden expressar en un llenguatge semblant al llenguatge matemàtic. Anem a veure la definició formal de dependència funcional:

>Given a relation R, a set of attributes X in R is said to functionally determine another set of attributes Y, also in R, (written X → Y) if, and only if, each X value in R is associated with precisely one Y value in R; R is then said to satisfy the functional dependency X → Y.

Aquesta definició no ens ha d'espantar perquè té una interpretació senzilla. El que ens diu és que hi ha una dependència funcional entre atributs quan un atribut o un conjunt d'atributs ens poden determinar els valor d'un altre atribut o conjunt d'atributs. Exemple, imaginem la taula 'Països', llavors l'atribut 'Codi ISO 3166' ens pot determinar 'Kilometres quadrats' i 'Número d'habitants'.

**Exercici**

1) Per poder entendre les formes normals a partir de la segona cal conèixer el concepte de dependència funcional, comprova que l'entens. Proposa un exemple de dependència funcional.

2) El concepte de dependència funcional no només apareix a la normalització. Per exemple, el SGBD MySQL té paràmetres de configuració que si els activem poden detectar les dependències funcionals que ens permetran enviar les consultes més abreujades a la base de dades. Aquí sota hi ha un fragment de la documentació, no cal que l'entenguis per ara, però si que cal que recordis que farem servir el concepte de dependència funcional en altres contextes diferents a la normalització.

>MySQL 5.7.5 and up implements detection of functional dependence. If the ONLY_FULL_GROUP_BY SQL mode is enabled (which it is by default), MySQL rejects queries for which the select list, HAVING condition, or ORDER BY list refer to nonaggregated columns that are neither named in the GROUP BY clause nor are functionally dependent on them. (Before 5.7.5, MySQL does not detect functional dependency and ONLY_FULL_GROUP_BY is not enabled by default. For a description of pre-5.7.5 behavior, see the MySQL 5.6 Reference Manual.)

( https://dev.mysql.com/doc/refman/5.7/en/group-by-handling.html )




>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. 
>

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.08.27 15:51:02
###### Editat per: daniel herrera 2016.08.30 16:58:07
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
