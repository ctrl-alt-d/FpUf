# Còpies de seguretat per la xarxa en Linux
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
Una de les tasques que pot fer falta en determinades ocasions és disposar d'alguna forma senzilla de poder fer còpies de seguretat o bé poder fer còpies de seguretat d'una quantitat petita de dades en un servidor remot 

###SSH
En aquests casos el protocol SSH i en especial les utilitats scp i sftp poden ser molt útils ja que no només permeten la còpia remota sinó que a més aquesta còpia es fa segura ja que és xifrada durant el seu trànsit per evitar que un atacant la pugui esnifar

```console
$scp *.txt usuari@servidor:/home/usuari/backup

```
Per poder automatitzar el procés és especialment important que s'hagi enviat la clau pública a l'ordinador remot o s'haurà d'especificar la contrasenya cada vegada que iniciem el procés de còpia 

###Sincronització de carpetes
 
En els llocs amb carpetes compartides és habitual que els usuaris puguin crear carpetes i fitxers nous segons els convingui. El sistema de còpia amb les utilitats scp de SSH pot ser adequat mentre la quantitat de fitxers no sigui molt gran. En els casos en que hi hagi una quantitat de dades molt gran el millor seria fer una còpia només de les dades que han canviat (o sigui sincronitzar les dues carpetes 

La utilitat clàssica de sincronització de carpetes en sistemes Unix és rsync 

```console
$ rsync carpeta1/ carpeta2/
```

Amb rsync no només es poden fer sincronitzacions en local sinó que també en poden fer en màquines remotes via SSH 

```console
$ rsync carpeta1/ usuari@servidor:carpeta2/
```

Hi ha molts entorns gràfics que fan servir *rsync* per fer còpies de seguretat o sincronitzar carpetes fent servir entorns gràfics 

Activitat
---------------
###Còpies de seguretat en la xarxa local amb SSH

1. Creeu en la vostra màquina una carpeta amb nom 'backup1' i poseu-hi uns quants arxius 
2. Entreu en un servidor remot amb SSH i feu-hi una carpeta amb el vostre nom
3. Des de la vostra màquina copieu la carpeta “backup1” fent servir scp cap al servidor en un directori que es digui "ssh" que estigui dins del que heu fet abans amb el vostre nom 
4. Elimineu dos arxius de la carpeta local i recupereu-los fent servir SCP.  

###Ús de rsync
En totes les comandes rsync feu servir -v per veure què està fent el programa

1. Creeu en la vostra màquina una carpeta amb nom 'backup2' i dins seu poseu-hi uns quants arxius 
2. Copieu la carpeta fent servir rsync en la carpeta de l'exercici anterior però en comptes de que es copiï a "SSH" que es faci en una altra anomenada "RSYNC".
3. Afegiu un arxiu nou a 'backup2' i sincronitzeu les dues carpetes. Què és el que s'ha copiat? Perquè? 
4. Elimineu un arxiu. Com ho podeu fer perquè també s'elimini del servidor?

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.3 1.4 1.6 1.7
* Continguts 1.2 1.6 1.7
---

###### Autor: Xavier Sala 2013.10.28 14:00:19
###### Editat per: daniel herrera 2013.10.29 13:37:01
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
