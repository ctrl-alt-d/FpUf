# Lluita de Pokémons salvatges
## DAW-MP03-UF6 - Exercici de POO. Introducció a la persistència en BD
Lluita de Pokémon salvatges
==============================
Tothom coneix la versió edulcorada dels Pokémons que s'ha mostrat en la sèrie o en els jocs però la realitat és molt més crua: Són animals molt salvatges.

En estat salvatge, els Pokémon que lluiten no s'entretenen a fer moviments, ni fan servir les habilitats per res sinó que es limiten a clavar garrotades. 

![Garrotades](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/pokemon1.png "Garrotada!")


Com són les batalles? 
-------------------------
La lluita consisteix en acabar amb els punts del contrari. 

* Al començar tots tenen 200 punts de vida
* Ataquen per torns. Però sempre comença el més ràpid (que és el que pesa menys)
* Sempre ataquen amb tota la força possible que tenen en el seu poder d'atac (Poders)
* Mai no fan servir la defensa, ni els atacs especials per res… Defensar-se és de covards

Evidentment, igual que en la sèrie de televisió l'atac es pot veure incrementar o reduït segons el tipus de Pokémon que sigui l'altre (Tipus_atac)

### Exemple de lluita entre Bulbasaur i Slowbro

1. Comença Bulbasaur (6,9 Kg) perquè pesa menys que Slowbro (78’2 Kg)
2. Bulbasaur ataca amb tota la seva **força d’atac (49)** que **es duplica** perquè Slowbro és de Water. Per tant l'atac és de 98!
3. Com que Slowbro encara té 102 punts de vida ataca a Bulbasaur

![Batalla](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/pokemon2.png "Les dues primeres fases")

El combat continua fins que algun dels Pokémon quedi sense vida. En aquest exemple després de tres atacs de Bulbasaur,  Slowbro es queda sense punts de vida. **Bulbasaur és el guanyador perquè encara li queden 50 punts**.

Tasca
--------------
1. El professor Von Schurrer, el millor especialista del món, ha descobert que en realitat en llibertat els Pokémon sempre van de dos en dos. I com que no pot calcular mentalment qui guanyarà necessita un programa que ho faci per ell.

![Combat!](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/pokemon3.png)

El programa ha de rebre els noms de les dues parelles que s'enfrontaran i dirà quina de les dues parelles és la guanyadora i quanta vida els hi queda

Els combats es fan de la següent forma:

* Lluiten un de cada parella fins que un dels dos perd
* El guanyador continua lluitant (amb la vida que li quedi) i lluita contra el company del perdedor.
* La lluita acaba quan una parella ha estat derrotada

Per saber les característiques de cada un dels Pokémon s'haurà de consultar la base de dades amb els estudis del professor de la que aquí teniu l'esquema:

![BDD](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/pokemon0.png "BDD eschema")

Una còpia de seguretat de la base de dades es pot [descarregar des d'aquí](https://drive.google.com/file/d/0B1USLpQ7TipGNWNpb2ZRQTZCLTA/view?usp=sharing)

---

#FpInfor #Daw #DawMp03 #DawMp03Uf06

---

###### Autor: Xavier Sala 2017.05.11 09:57:36
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
