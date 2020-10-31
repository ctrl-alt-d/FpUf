# Model Conceptual de Dades - Els partidillos
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
Aquest exercici consisteix a construir el MCD a partir de les relacions de la base de dades.

Observa aquestes taules:
equip ( id (pk), nom )
camp( id (pk), nom )
jornada( numeroJornada (pk), dataOrientativa )
partit( numeroJornada (pk, fk a jornada), campPrevist (pk, fk a camp) )
equipJugaPartit( numeroJornada (pk, fk a partit), campPrevist (pk, fk a partit), equip (pk), 
golsMarcats, esEquipLocal )

**Fés el MCD per poder tenir una visió global de l'estructura de la base de dades**

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2013.09.07 10:00:30
###### Editat per: daniel herrera 2013.09.07 10:00:30
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
