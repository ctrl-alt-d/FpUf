# Serveis REST - País Província Municipi
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Es tracta de fer dos serveis REST que retornin JSON, un amb 'Municipis' i un altre amb 'Municipis'. Aquests serveis es consumiran des del client per millorar l'esperiència d'usuari del formulari d'entrar dades de 'Persona'.

Aquests són els nostres models:

* `País` ( `Codi ISO` **PK**, `Nom` )
* `Província` ( `Id Província` **PK**, `Codi ISO` **FK** a país, `Nom` )
* `Municipi` ( `Id Municipi` **PK**, `Id Província` **FK** a província, `Nom` )
* `Persona` ( `Nif`  **PK**, `Nom`, `Carrer`, `Id Municipi` **FK** a Municipi ) 

El primer servei REST rebrà dos paràmetres: Codi ISO país i 'term'. Retornarà totes les províncies del país informat que al seu nom continguin 'term'.

El segon servei REST rebrà dos paràmetres: Id Província i 'term'. Retornarà tots els municipis de la província informada que al seu nom continguin 'term'.

A la vista `Persona` recorda esborrar `Província` i `Municipi` quan es canvii el país. Recorda esborrar `Municipi` quan es canvii `Província`.

**Tecnologia**

Aquest exercici es pot desenvolupar amb qualsevol framework web, exemple:

* Utilitza Microsoft EF i dbcontext per a crear els models.
* Utilitat Microsoft MVC per a crear l'aplicació web. Tres controladors: un per a Persona, un per a Municipi i un darrer per a província ( opcionalment un altre per a país).
* Utilitza la llibreria javascript Select2 per crear els controls d'usuari.



---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2015.03.20 14:16:20
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
