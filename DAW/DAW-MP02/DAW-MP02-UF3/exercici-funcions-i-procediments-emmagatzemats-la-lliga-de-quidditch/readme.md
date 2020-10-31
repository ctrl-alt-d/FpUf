# Exercici funcions i procediments emmagatzemats: La lliga de quidditch
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
Aquests són els tipus de jugadors de quidditch:

>Un guardià, dos copejadors, 3 caçadors i un cercador. El guardià és el porter que s'encarrega d'evitar que l'equip contrari introduïu la quaffle en els cèrcols del seu respectiu equip. Els copejadors són els encarregats de repel·lir les bludgers, per protegir al seu equip d'elles. Els caçadors són els encarregats de procurar introduir la quaffle a través dels cèrcols contraris.

I aquestes són les possibles infraccions:

Rowling ha escrit que hi ha 700 faltes en el Quidditch llistades pel Departament d'Esports i Jocs Màgics, però la majoria d'elles no estan obertes al públic, ja que el Departament tem que els mags que llegeixin la llista de faltes "podrien tenir males idees". Es diu que totes les faltes van ocórrer durant el primer Mundial de Quidditch. Aparentment, la majoria ara són impossibles de cometre per la regla imposada respecte a l'ús de les varetes contra els oponents (imposada en 1538). Les faltes més comunes estan relacionades aquí:

**Blagging**

* Aplicat a: tots els jugadors.
* Descripció: els jugadors no poden agafar el raspall de l'escombra d'un oponent per minorar el vol (Draco Malfoy comet aquesta falta en Harry Potter i el presoner d'Azkaban, evitant que Harry atrapi la Snitch).

**Blatching**

* Aplicat a: tots els jugadors.
* Descripció: els jugadors no poden volar amb la intenció d'estavellar contra un altre (el cercador substitut de Slytherin, Harper, trenca aquesta regla al xocar contra Harry després d'insultar Ronald Weasley. Això passa en el sisè llibre, Harry Potter i el Misteri del príncep).

**Blurting**

* Aplicat a: tots els jugadors.
* Descripció: els jugadors no poden subjectar el mànec de les escombres per treure de curs a un oponent.

**Bumphing**

* Aplicat a: copejadors.
* Descripció: els golpeadores no poden enviar les bludgers cap als espectadors (encara que Harry a manera de broma li ordena a un dels seus copejadors enviar-li una a Zacharias Smith pels seus comentaris en Harry Potter i el Misteri del Príncep), ni al Guardià, llevat que la quaffle és dins l'àrea d'anotació (en la primera pel·lícula, però, Marcus Flint, un Caçador, comet aquesta falta amb un bat de Golpeador, i Madam Hooch el penalitza per això).

**Cobbing**

* Aplicat a: tots els jugadors.
* Descripció: els jugadors no poden fer ús excessiu dels seus colzes contra els oponents (Marcus Flint, Caçador de Slytherin, comet aquesta falta contra la Caçadora de Gryffindor, Angelina Johnson, en Harry Potter i la cambra secreta).

**Flacking**

* Aplicat a: Guardians.
* Descripció: no poden defensar els pals de gol des del darrere empenyent les Quaffles fora dels cèrcols: han defensar des del front.

**Haversacking**

* Aplicat a: Caçadors.
* Descripció: no han de fer contacte amb la quaffle mentre passi a través d'un cèrcol (la quaffle ha de ser llançada a través del cèrcol).

**Quaffle-Pocking**

* Aplicat a: Caçadors.
Descripció: no han de sabotejar la quaffle de cap manera (per exemple, punxar perquè caigui més ràpid o vagi en ziga-zaga).

**Snitchnip**

* Aplicat a: tots els jugadors excepte els Cercadors.
* Descripció: tocar o atrapar la Snitch Daurada.

**Stooging**

* Aplicat a: Caçadors.
* Descripció: no es permet més d'un sol Caçador dins de l'àrea d'anotació.

Feina:
===

1) Crea i ompla les següents taules a la base de dades segons el que has llegit anteriorment:

```sql
Rols( nom pk, quantitat, funcio )
TipusInfraccions( nom pk, descripcio )
RestriccioInfraccioRol( rol pk fk, tipusInfraccio pk fk )
```

2) Crea les següents taules sense posar dades:

```sql
Equip( Nom pk, Localitat )
Partit( data_i_hora pk, equipLocal pk fk, equip visitant fk, marcador_local, marcador_visitant )
Jugador( Equip pk fk, numero pk, nom, rol fk, esTitular )
Incidencia( partit_data_i_hora pk fk1, partit_equipLocal pk fk1, moment_infraccio pk, Jugador_equip fk2, Jugador_numero fk2, tipusInfracció fk3 ) 
```

3) Crea les següents funcions:

```sql
numTitulars( rol, equip ) --retorna quants titulars d'un determinat rol hi 
                          --ha en un equip
puntsALaLliga( equip ) --   total de partits guanyats * 3
                       -- + total de partits empatats * 1
diferenciaDeGols( equip ) --gols marcats - gols encaixats
```

4) Crea els següents procediments emmagatzemats i prova'ls:

* `CreaEquip`: Se li passen dos paràmetres i crea un equip.
* `CreaPartit`: Se li passen els paràmetres i crea un partit. Deixa els marcadors a 0.
* `AnotaGol`: se li passen els paràmetres i anota 10 punts.
* `AnotaSnitch`: se li passen els paràmetres i anota 50 punts.
* `AfegeixJugadorEquip`: Se li passen els paràmetres i afegeix un jugador a un equip. Comprova que no hi hagin més titulars d'un determinat rol dels permesos. Comprova que no hi hagi més de 12 jugadors per equip.
* `AnotaInfracció`: Se li passen els paràmetres i s'assigna una infracció a un jugador d'un partit. Important comprovar que la infracció es pot assignar a aquell rol.


Nota: la informació sobre el Quidditch ha estat obtinguda del [Quidditch Wikipedia](https://ca.wikipedia.org/wiki/Quidditch).

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2018.03.16 17:38:21
###### Editat per: daniel herrera 2018.03.19 18:51:08
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
