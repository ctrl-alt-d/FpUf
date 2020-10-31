# Batalla campal!
## DAW-MP03-UF4 - Exercici de Programació orientada a objectes. Fonaments
Batalla-campal
==============

Introducció
----------------------
L'objectiu del programa és representar la batalla entre dos exercits diferents formats per soldats que mataran i moriran xocant amb els altres soldats.

* Això és un exercici que he proposat als alumnes per aprendre Programació Orientada a Objectes
* El mòdul s'imparteix en Java
* L'única dependència és la llibreria de Java de l'ACM (http://cs.stanford.edu/people/eroberts/jtf/)

Es pot veure un exemple del programa en execució en un [vídeo de Youtube](http://youtu.be/hspq83vK7-Y)

Formació inicial
--------------------------------
Al començament de la batalla cada exèrcit es posarà en files en un dels costats de la pantalla i es mourà en direcció a l'altre exèrcit. Per començar els exèrcits es dividiràn en 6 files en les que cada exèrcit hi posarà aleatòriament els seus soldats.

![Formació inicial](https://raw.githubusercontent.com/utrescu/Batalla-campal/master/batalla1.png)

En el moment en que quedin menys de 6 soldats en un dels dos exèrcits les files es reduiran a tantes com soldats tingui l'exercit més petit.

![Formació modificada](https://raw.githubusercontent.com/utrescu/Batalla-campal/master/batalla2.png)

Avançar
---------------------------
En cada passada tots els soldats d'un exèrcit aniran avançant un número aleatori de píxels. En cas en que un soldat caigui damunt de un enemic (el matarà) i desapareixerà de la pantalla.

![Matar soldats](https://raw.githubusercontent.com/utrescu/Batalla-campal/master/batalla3.png)

En l'avenç hi ha restriccions:
* Quan es mata un enemic no es pot avançar més de la posició que ocupava aquest
* No es poden matar soldats amics. Els soldat del darrera mai podrà avançar el del davant.

Un cop ha avançat un exercit avançarà l'altre en les mateixes condicions
* Per evitar que cap dels dos exèrcits tingui avantatge abans de cada ronda es decidirà aleatòriament quin dels dos exèrcits es mou primer

Quan tots els soldats dels dos exèrcits arribin a l'altre costat es tornaran a posar en formació en l'altre costat i avançaran en sentit contrari.

Final del joc
----------------------
El joc acabarà quan un dels dos exèrcits es quedi sense soldats

![Final de la batalla](https://raw.githubusercontent.com/utrescu/Batalla-campal/master/batalla4.png)


---

#FpInfor #Daw #DawMp03 #DawMp03Uf04

---

###### Autor: Xavier Sala 2015.10.10 22:52:49
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
