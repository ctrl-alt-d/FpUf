# SQL Exercicis 5.3: Selects: where i group by. Partits de futbol
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Observa aquestes taules:
    
    equip ( id (pk), nom )
    camp( id (pk), nom )
    jornada( numeroJornada (pk), dataOrientativa )
    partit( numeroJornada (pk, fk1 a jornada), campPrevist (pk, fk2 a camp) )
    equipJugaPartit( numeroJornada (pk, fk1 a partit), 
                     campPrevist (pk, fk1 a partit), equip ( fk2 a equip), 
                     golsMarcats, esEquipLocal (pk) )

1. Fés el MCD per poder tenir una visió global de l'estructura de la base de dades
1. Fes els create tables. Amb claus primàries i foranes.
2. Inserta dades. Inserta al menys `Mestalla` i el `CampNou`
2. Total de gols marcats a Mestalla. (Join o subconsulta per saber id de 'Mestalla')
3. Total de gols marcats per Equip.
3. Total de gols marcats a cada camp.
4. Llistat d'equips que han jugat al 'CampNou'
5. Llistat de partits disputats amb nom dels equips i resultat final.
6. Mostra els equips que han marcat més de 3 gols (en tota la temporada)
7. Mostra els partits amb més de 3 gols ( nivell de dificultat alta )
8. Mostra els equips que han marcat més gols que la mitjana dels equips calculdada com la suma de tots els gols dividit pel número de partits ( nivell de dificultat alta )
9. Mostra els camps on s'han marcat més gols de un 70% la mitjana de gols que es marquen per camp (calculada com suma de gols per camp dividit per número de camps )

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2013.09.07 14:36:20
###### Editat per: daniel herrera 2018.01.29 18:48:04
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
