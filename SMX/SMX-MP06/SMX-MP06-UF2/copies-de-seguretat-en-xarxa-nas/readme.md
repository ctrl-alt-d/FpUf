# Còpies de seguretat en xarxa: NAS 
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
Introducció
==============
Per emmagatzemar dades en local existeix un ventall de possibilitats. Les més comuns solen ser tenir algun tipus de maquinari per fer l'emmagatzematge. Fa uns anys els requeriments de capacitat eren relativament petits i es solien usar sistemes connectats a determinats servidors claus

Al principi el més corrent era tenir sistemes d'emmagatzematge a través de la xarxa. Això permet que els diferents equips de la xarxa puguin emmagatzemar les còpies de seguretat en un punt

![Còpies en xarxa](http://imageshack.us/a/img443/4418/gtg2.png "còpies en xarxa")

Però l'increment tant gran de dades fa que la tendència sembla estar en tenir algun sistema descentralitzat que permeti absorbir tot l'ample de banda dades, no tingui problemes de rendiment i a més s'evita la possibilitat de tenir un sol punt de fallada
SAN
-----
La proliferació de servidors amb sistemes diferents i mesclats pot fer complexa l'administració dels sistemes de còpies de seguretat. 

![SAN](http://imageshack.us/a/img12/3033/lxg5.png "SAN")

Una xarxa SAN (Storage Area Network) és una xarxa d'alta velocitat separada de la xarxa de treball de l'organització en la que a través de connexions de maquinari especials les dades es poden moure's entre emmagatzematges sense que això afecti a la xarxa principal

Les còpies de seguretat poden ser controlades de forma centralitzada i normalment a través d'algun entorn web

NAS
---------------------
Els dispositius NAS (Network-attached Storage) són servidors de fitxers dedicats que permeten un emmagatzematge d'accés ràpid i d'alta disponibilitat. 
El més habitual és que siguin administrats via algun entorn web

###NAS de programari
Els NAS de programari són ordinadors tradicionals que es fan servir com a NAS. No funcionen com els servidors tradicionals, els NAS normalment tenen el seu propi sistema operatiu.

![FreeNAS](http://imageshack.us/a/img823/1245/7lfj.png "FreeNAS")

Hi ha diferents sistemes NAS de codi obert com per exemple FreeNAS o OpenFiler

###NAS de maquinari
A part de les solucions de programari en el mercat existeixen diversos sistemes de maquinari que funcionen com a sistemes d'emmagatzematge

![HW NAS](http://imageshack.us/a/img853/4015/5wgn.png "HW NAS")

Per exemple hi ha sistemes de backup amb discs durs extraïbles com 

    Exemple: PowerVault 114X RD1000 Rack Enclosure

O sistemes amb cintes que proporcionen una capacitat d'emmagatzematge superior a un preu molt inferior a costa de reduir-ne la velocitat d'accés

    Exemple: PowerVault ML6000

Tasca
=============

Hardware dedicat de còpies de seguretat
-------------------------------------------

1. Fes un pressupost comparatiu entre un SERVIDOR DE BACKUP AMB DISC DUR EXTRAÏBLE i un SERVIDOR DE CINTES amb la capacitat estàndard de cada dispositiu. Al pressupost ha d'incloure, com a mínim, 5+1 unitats extraïbles ( dies de la setmana laborables + una externa setmanal fora del local ).

NAS de programari
--------------------
2. Localitzeu alguns sistemes NAS de codi obert

3. Expliqueu el procediment d'instal·lació d'algun d'aquests NAS en una màquina virtual 

4. Poseu un fitxer en el sistema d'emmagatzematge del NAS

5. Expliqueu com es pot fer per recuperar aquest fitxer des d'una altra màquina

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.3 1.4
* Continguts 1.2 1.3
---

###### Autor: Xavier Sala 2013.11.04 10:06:27
###### Editat per: Xavier Sala 2013.11.04 10:06:26
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
