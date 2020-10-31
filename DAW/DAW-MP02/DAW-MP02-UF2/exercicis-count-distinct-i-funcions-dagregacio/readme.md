# SQL Exercicis 5.4: Exercicis count distinct i funcions d'agregació
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
Exercici 1
===============

Una empresa té una taula de treballadors amb aquesta estructura:

```bash
treballadors ( NSS (PK), nom, NSS_del_meu_jefe (FK a treballadors pot ser null)
```

Escriu en format de taula com queda si tenim aquestes dades:

* La Marta té NSS 100 i no té jefe.
* La Juana té NSS 200 i no té jefe.
* En Pere té NSS 300 i la seva jefa és la Marta.
* En Joan té NSS 400 i el seu jefe en en Pere.
* En Josep té NSS 500 i la seva jefa és la Marta.

Contesta:

* 1) Pot un treballador d'aquesta empresa tenir més d'un Jefe?
* 2) Si per ser jefe cobre més, quin(s) és(són) el(s) treballador(s) que cobra(en) menys de l'empresa?
* 3) Escriu una select per saber quants treballadors són jefes d'algun altre treballador, sense enumerar-los.

Exercici 2
===============

Tenim una gossera amb gosos que poden ser de raça o no. L'estructura és la següent:

```bash
Gos: num_xip (pk), nom, preu, codi_raça (fk a Raça pot ser null)
Raça: codi_raça (pk), nom
```

* 4) Escriu una select per saber quantes races diferents tenim actuament a la gossera. Sense enumerar les races.
* 5) Escriu una select per saber quants gossos de cada raça tenim a la gossera. Resultat: nom de la raça i número de gossos d'aquella raça.
* 6) Escriu una select per saber quan val el gos més car i el més barato de cada raça. També el preu mitjà dels gossos d'aquella raça. Resultat: nom de la raça i els valors.

**Solució**

* [SQL: Exercici funcions d'agregació](https://youtu.be/uyGyobkZx8Y)  27' YT

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2018.01.26 14:23:05
###### Editat per: daniel herrera 2018.01.29 15:33:47
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
