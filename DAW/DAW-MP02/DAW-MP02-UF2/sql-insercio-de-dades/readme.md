# SQL: Inserció de dades
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Observa aquestes taules:
    
    equip ( id (pk), nom )
    camp( id (pk), nom )
    jornada( numeroJornada (pk), dataOrientativa )
    partit( numeroJornada (pk, fk1 a jornada), campPrevist (pk, fk2 a camp) )
    equipJugaPartit( numeroJornada (pk, fk1 a partit), 
                     campPrevist (pk, fk1 a partit), equip ( fk2 a equip), 
                     golsMarcats (permet nulls), esEquipLocal (pk) )

1.- Fés el MCD per poder tenir una visió global de l'estructura de la base de dades

2.- Fes els create tables. Amb claus primàries i foranes.

3.- Inserta aquests equips:

```bash
Barça
València
Osasuna
Numància 
```

4.- Inserta els camps dels equips esmentats.

5.- Inserta 3 jornades.

6.- Inserta aquests partits al camp de l'equip que juga a casa, deixa els gols marcats a NULL:

```bash
1a Jornada:
Barça - Numància
Osasuna - València
```

    2a Jornada:
    Osasuna - Barça
    València - Numància

    3a Jornada:
    Barça - València
    Osasuna - Numància

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2018.01.29 15:47:25
###### Editat per: daniel herrera 2018.02.05 18:22:53
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
