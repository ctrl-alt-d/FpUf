# Carrera de camells
## DAW-MP03-UF4 - Exercici de Programació orientada a objectes. Fonaments
Objectius: Aprofitar l'herència per desenvolupar un programa fent servir una llibreria

Introducció
======================
L'objectiu és crear un programa que representi el joc de carreres de camells de les fires. El joc de carreres de camells consisteix en que cada jugador tira una pilota i avança tantes posicions com el número en el que ha aconseguit entrar la pilota. Si la pilota no entra no avança..

![Carrera de camells](http://img855.imageshack.us/img855/1889/7app.jpg "enter image title here")

Per fer aquest programa és recomana fer servir la llibreria de [Java de l'ACM JTF](http://www-cs-faculty.stanford.edu/~eroberts/jtf/)

Activitat
======================

1. Desenvolupeu el programa per representar gràficament la carrera de camells
    1. Podeu representar els jugadors tant amb imatges com amb figures però poden ser com a màxim de 50 píxels d'ample
    2. Cada jugador tindrà una possibilitat d'avançar o no, que s'avaluarà primer, i si ha d'avançar ho farà un número aleatori de píxels de 1 a 15
    3. La sortida serà el costat esquerra de la pantalla i guanya el jugador que toqui el costat dret de la finestra
    4. La finestra serà de 900px d'ample
    5. Cal acabar la ronda abans de poder donar per acabada la partida.
    6. Si hi ha un empat guanya el que li hagin sobrat més punts 

2. Modifiqueu el programa anterior perquè permeti als camells “professionals” participar en les carreres.

    1. Hi haurà camells Ràpids que en cas de que el número que treguin sigui el valor màxim avançaran el doble de píxels (15 --> avança 30)
    2. En canvi els camells Fondistes sempre obtindran un valor entre [5,10]
    3. Els camells AntiSenars només avançaran normalment si el valor que treuen és un número parell ( si el valor és senar avançaran 2 píxels)
    4. Els camells Flipats avançaran un cop endavant i un cop enrere

![Carrera!](http://imageshack.us/a/img268/1867/6yqj.png "Carrera")

Solució: [Camells](https://github.com/utrescu/camells/tree/herencia)


---

#FpInfor #Daw #DawMp03 #DawMp03Uf04

* Resultats d'aprenentatge 1.a 1.b 1.c 1.d 1.e 1.f 2.a 2.b 2.c 2.d 2.e 2.f .2.g 2.h 2.j 3.a 3.e 3.g 3.h 3.i
* Continguts 3.1 3.2 3.3
---

###### Autor: Xavier Sala 2013.11.18 15:45:43
###### Editat per: Xavier Sala 2013.11.18 16:57:22
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
