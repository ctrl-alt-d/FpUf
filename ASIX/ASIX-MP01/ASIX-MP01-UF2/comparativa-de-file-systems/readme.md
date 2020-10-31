# Comparativa de File Systems
## ASIX-MP01-UF2 - Exercici de Gestió de la informació i de recursos en una xarxa
**Introducció**

Es tracta de crear un joc de proves per tal de mesurar el rendiment de diferents sistemes de fitxers coneguts.


**Mètriques**

 * Temps per a la creació de fitxers grans (250MB, 150MB i 50MB) i petits (1KB, 5KB i 10KB) en els diferents sistemes de fitxers i cadascun amb diferents clústers.
 * Temps en moure els fitxers d’una carpeta a una altre.
 * Temps en copiar el fitxer
 * Temps en eliminar fitxers

**Entregables**

 * Scripts utilitzats per a la automatització de les proves. Han de constar de:
     * Comandes per a crear i formatejar el sistema de fitxers ( parametritzable ).
     * Comandes per a realitzar les accions a mesurar ( crear els fitxers, esborrar-los, moure'ls, ... )
     * Comandes per anotar les mètriques en fitxer de log independent.
 * Taules i gràfics comparatius dels resultats obtinguts.
 * Conclusions.

**Exemples**

Exemples de gràfics comparatius:

![Pràctica file systems](http://i.imgur.com/FYHWhaY.png)
![Pràctica file systems](http://i.imgur.com/ixEBAdg.png)
![Pràctica file systems](http://i.imgur.com/s2bce3W.png)
![Pràctica file systems](http://i.imgur.com/Ty2iesG.png)
![Pràctica file systems](http://i.imgur.com/C5AcJHF.png)
![Pràctica file systems](http://i.imgur.com/kVOnA2X.png)
![Pràctica file systems](http://i.imgur.com/BOeuKbX.png)
![Pràctica file systems](http://i.imgur.com/WdEirhe.png)

Exemples de conclusions:

 * EXT4 treballa de forma més regular amb els tres tipus de clúster.
 * REISER (amb un clúster de 4k) és el que més ràpid executa totes les accions descrites.
 * NTFS al no ser un sistema de fitxers natural de LINUX no és molt òptim excepte a l’hora d’esborrar arxius de gran mida.
 * Amb els diferents sistemes de fitxers, a l’hora de treballar amb fitxers amb una mida inferior a la del clúster o una mica més superior veuen incrementat el temps d’execució.
 * Tal com s'aprecia al llarg de tot l'estudi, no hi ha un sistema de fitxers que sigui el millor en tot. Sistemes de fitxers com XFS, presenten un bon comportament alhora de crear fitxers però en canvi presenta resultats molt pitjors, respecte la resta, quan es tracta de moure fitxers.
 * D'altra banda, EXT4 presenta un rendiment més estable atès que malgrat no ser el millor en totes les proves tampoc és el pitjor en cap d'elles (tret del test de còpia de fitxers).
 * D'altra banda, des del punt de vista d'espai utilitzat, és l'únic sistema que reserva un 5% de l'espai disponible per al root (directori LOST+DIR). Tanmateix, si s'elimina aquest 5% es comporta exactament igual que la resta independentment de la mida del clúster.
 * El fet de modificar la mida del clúster, tal com demostren les dades obtingudes, representa un empitjorament del comportament dels sistemes en totes les proves.
 * Aquest fet constitueix un resultat esperat atès que segurament sigui per aquesta la raó per la qual la mida per defecte és de 4K.
 * Finalment, en el cas de NTFS i REISER, presenten bons resultats alhora d'eliminar dades però si es tenen en comte la resta de proves es pot observar que ho fan en detriment del temps emprat en la copia i el moviment de fitxers.
 * En definitiva, després de realitzar l'estudi en qüestió, el sistema de fitxers que sembla més òptim a nivell d'usuari és l'EXT4. Segurament, per aplicacions més concretes el resultat no seria el mateix però en aquest cas seria necessari elaborar un nou estudi.

Crèdits: *Alumnes GS informàtica Ins Ausiàs March, Barcelona*



---

#FpInfor #Daw #Asix #Dam #AsixMp01 #DamMp01 #DawMp01 #AsixMp01Uf02 #DawMp01Uf02 #DamMp01Uf02

* Resultats d'aprenentatge 1.1 .14
* Continguts 1.7
---

###### Autor: daniel herrera 2014.02.17 14:38:34
###### Editat per: daniel herrera 2014.02.17 15:16:07
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
