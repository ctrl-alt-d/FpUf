# Prevenció i detecció d'atacs "Man in the middle" en xarxes locals
## SMX-MP06-UF5 - Exercici de tallafocs i monitoratge de xarxes.
#Avís

L'objectiu d'aquesta activitat és demostrar la facilitat amb que es pot fer un atac per a interceptar informació sense xifrar en una xarxa local. Després cal que l'alumne busqui i implanti formes de prevenir-lo i detectar-lo.

Com deia el tiet Ben de l'Spiderman: 

*"Tenir un gran poder implica una gran responsabilitat".*

#Recursos
[Eines de hacking en xarxes d'àrea local
](https://www.youtube.com/watch?v=MOuS5JC24mM) 

#Activitat
En una màquina virtual amb GNU/Linux, instal·leu el paquet **dsniff**.

Activeu l'encaminament IP en la màquina de forma permanent. Expliqueu com ho heu fet.

Amb l'eina **arpspoof**, feu un atac Man in the middle (MITM) a la vostra màquina física. Expliqueu com ho heu fet i mostreu captura que demostri que heu interceptat un text sense xifrar.

Cerqueu formes de **prevenir que us facin un atac MITM** amb l'enverinament ARP i proveu-les. Mostreu com ho heu fet i demostreu que ho heu aconseguit.

Cerqueu **formes de detectar els atacs MITM** amb enverinament ARP i proveu-les. Mostreu com ho heu fet i la captura que demostri la detecció de l'atac.

#Pistes

Una forma de prevenir un MITM amb enverinament ARP té a veure amb la manipulació de la taula ARP de la possible víctima.

Altres formes més sofisticades impliquen la instal·lació de programes com: HIDS: Host Intrusion Detection System (en un sol dispositiu), NIDS: Network Intrusion Detection System (en una xarxa)

En aquesta activitat serà suficient que instal·leu un programa en host que detecti l'atac MITM (també n'hi ha per mòbils).

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf05

* Resultats d'aprenentatge 1.d, 1.f
---

###### Autor: Carles Caño 2017.03.27 13:24:02
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
