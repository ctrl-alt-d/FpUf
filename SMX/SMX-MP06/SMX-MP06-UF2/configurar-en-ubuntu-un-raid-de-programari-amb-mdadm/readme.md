# Configurar en Ubuntu un RAID de programari amb mdadm
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
##Materials de referència
- Llista de reproducció (5 vídeos, 42m) [Sistemes d'emmagatzematge RAID](http://www.youtube.com/watch?v=L0xaKAO00TE&list=PLtJgRey-A7fRstGnL7ABljKxNl3P9S2jI)
- Vídeo (5m21s) [
Building an RAID-5 Volume on 5 usb floppy drives - PART 1/2](http://vimeo.com/13758987)
- Vídeo (10m) [Building an RAID-5 Volume on 5 usb floppy drives - PART 2/2](http://vimeo.com/13799310)
##Observacions

- Indiqueu les comandes necessàries així com altres canvis que feu al sistema per a fer el que se us demana.

- Feu aquesta pràctica amb una màquina virtual d'Ubuntu.

- Necessitareu de 2 a 4 discos durs virtuals per a fer aquesta activitat, depenent del RAID que us hagi tocat fer.

- El professor us indicarà quin RAID heu d'implementar cadascun de vosaltres.

##Activitat
1. Instal·leu el paquet **mdadm**. Escriviu el nivell de RAID que heu d'implementar: ______________
2. Com a usuari root, particioneu els discos durs virtuals amb **fdisk**. Heu d’establir l’identificador del sistema (tipus de partició) a **Automatic RAID**.
3. ¿Les particions que utilitzeu poden ser de mides diferents o han de ser iguals? Raona la resposta.
4. Amb la comanda **mdadm** crea un RAID de nivell 0, 1, 10, 4, 5 o 6 (segons quin t'hagi tocat). Fes una captura de la comanda i explica per a què serveix cada paràmetre.
5. Amb quina comanda pots comprovar que el RAID està creat? Mostra la captura amb la informació que et retorna.
6. Formata el RAID amb el sistema de fitxers que t'hagi estat assignat: _____________.
7. Munta el RAID des de línia de comandes a la carpeta /media/m6 (crea abans la carpeta).
8. Copia arxius i crea carpetes a la carpeta /media/m6 (compte amb els permisos de la carpeta, si no estan bé, no podràs escriure-hi) Com pots consultar l'estat actual del RAID?
9. Amb quina comanda pots eliminar un disc del RAID? Fes-ho i consulta l'estat actual i assenyala on s'indica que hi ha un problema.
10. Amb el RAID que has hagut de muntar, què ha passat quan has tret el disc en l'exercici anterior? Pots accedir a les dades? Justifica la resposta. Com pots fer que tot torni a la normalitat?
11. Quins canvis has de fer al teu sistema Linux per a que el RAID que has creat es munti automàticament a l'iniciar el sistema.
12. Quan hagis acabat, demana al professor que t'assigni un altre RAID i repeteix els exercicis 4 a 11.

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.d
* Continguts 3
---

###### Autor: Carles Caño 2013.10.26 22:34:26
###### Editat per: Carles Caño 2013.10.26 22:34:26
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
