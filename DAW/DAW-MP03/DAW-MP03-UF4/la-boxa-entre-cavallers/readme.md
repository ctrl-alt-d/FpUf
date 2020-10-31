# La boxa entre cavallers
## DAW-MP03-UF4 - Exercici de Programació orientada a objectes. Fonaments
# Boxa entre cavallers

La “boxa entre cavallers” es lleugerament més educada que la tradicional. En aquest tipus de boxa els contendents es claven cops però ho fan de forma ordenada

El combat consisteix en anar repetint el mateix procés:

* Primer pica un mentre l’altre es protegeix
* Després pica el segon mentre el primer es protegeix

El combat acaba quan un dels dos cau perquè ha rebut molts cops en llocs desprotegits

## Cops i protecció

Cada boxejador pot picar en quatre llocs diferents del seu contrincant.

![Cops](https://raw.githubusercontent.com/utrescu/Boxa/master/atacs-boxa.png "On pot rebre?")

Les proteccions que pot fer un boxejador són perfectes. Això vol dir que si rep un cop en una protecció no rebrà cap mal.

Desafortunadament el que es protegeix només pot protegir tres llocs. Això vol dir que sempre pot rebre un cop en un lloc desprotegit

## Activitat: El combat

Es demana que desenvolupeu, fent servir orientació a objectes, un programa que permeti simular el funcionament del combat de boxa entre cavallers i el vagi radiant per pantalla.

```bash
$ java -jar Boxa-1.0-SNAPSHOT.jar
MatxacaCaps(5) cop bloquejat per DestrossaPilotes(5)
DestrossaPilotes(5) cop bloquejat per MatxacaCaps(5)
MatxacaCaps(5) cop bloquejat per DestrossaPilotes(5)
DestrossaPilotes(5) cop bloquejat per MatxacaCaps(5)
MatxacaCaps(5) cop al cap de DestrossaPilotes(4)
DestrossaPilotes(4) cop bloquejat per MatxacaCaps(5)
MatxacaCaps(5) cop bloquejat per DestrossaPilotes(4)
DestrossaPilotes(4) cop bloquejat per MatxacaCaps(5)
MatxacaCaps(5) cop al costat dret de DestrossaPilotes(3)
DestrossaPilotes(3) cop al costat esquerra de MatxacaCaps(4)
MatxacaCaps(4) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop bloquejat per MatxacaCaps(4)
MatxacaCaps(4) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop bloquejat per MatxacaCaps(4)
MatxacaCaps(4) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop a la panxa de MatxacaCaps(3)
MatxacaCaps(3) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop bloquejat per MatxacaCaps(3)
MatxacaCaps(3) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop al costat esquerra de MatxacaCaps(2)
MatxacaCaps(2) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop bloquejat per MatxacaCaps(2)
MatxacaCaps(2) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop a la panxa de MatxacaCaps(1)
MatxacaCaps(1) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop bloquejat per MatxacaCaps(1)
MatxacaCaps(1) cop bloquejat per DestrossaPilotes(3)
DestrossaPilotes(3) cop bloquejat per MatxacaCaps(1)
MatxacaCaps(1) cop al costat esquerra de DestrossaPilotes(2)
DestrossaPilotes(2) cop bloquejat per MatxacaCaps(1)
MatxacaCaps(1) cop al costat esquerra de DestrossaPilotes(1)
DestrossaPilotes(1) cop bloquejat per MatxacaCaps(1)
MatxacaCaps(1) cop bloquejat per DestrossaPilotes(1)
DestrossaPilotes(1) cop bloquejat per MatxacaCaps(1)
MatxacaCaps(1) cop bloquejat per DestrossaPilotes(1)
DestrossaPilotes(1) cop bloquejat per MatxacaCaps(1)
MatxacaCaps(1) cop bloquejat per DestrossaPilotes(1)
DestrossaPilotes(1) cop al costat dret de MatxacaCaps(0)
MatxacaCaps(0) està KO!
 
Ha guanyat en DestrossaPilotes
```

---

#FpInfor #Daw #DawMp03 #DawMp03Uf04

---

###### Autor: Xavier Sala 2015.10.10 22:56:12
###### Editat per: daniel herrera 2015.10.16 15:37:07
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
