# Independència física i lògica als sistemes gestors de base de dades.
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Un dels principals reptes dels sistemes gestors de base de dades és el de mantenir la indepèndència lògica i física de les dades. És a dir, que els programes que realitzen consultes a la base de dades no es vegin afectats per canvis a la organització física de les dades o a l'estructura lògica de les mateixes.

**Exercicis**

1. Quan creem un índex a una relació de la base de dades, estem canviant l'estructura física o lògica?
2. Quan declarem un `cluster index` el SGBD ordena les dades a disc per la clau que definim, per aquest motiu només pot haver un índex d'aquesta mena per taula. Si esborrem un cluster index, estem fent un canvi físic o lògic?
3. Suposem que a la relació de clients teniem els camps 'telèfon', 'mail' i 'fax'. Però ara es determina que cal trencar aquesta relació amb dues i tenir per una banda la relació de `clients` i per una altre banda la relació de `adreces de contacte de client` ( amb els camps tipus d'adreá i adreça ). És aquest un canvi lògic o físic?
4. Quina independència creus que costa més de mantenir, la independència física o la lògica?
5. En un SGBD una vista és: *In database theory, a view is the result set of a stored query on the data, which the database users can query just as they would in a persistent database collection object.* Quina de les dues independències creus que ens soluciona una vista, la física o la lògica?







*Definició de vista extreta de la wikipedia: https://en.wikipedia.org/wiki/View_(SQL)*


>
>######Aquest exercici està extret del llibre [Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor.
>

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.05.17 08:59:13
###### Editat per: daniel herrera 2016.08.30 16:50:31
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
