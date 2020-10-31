# Còpies de seguretat tradicionals en Unix
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
Introducció
--------------
En els sistemes Unix tradicionalment s'ha fet servir la comanda 'tar' per fer còpies de seguretat. La comanda 'tar' crea un arxiu de diversos simplement encadenant-los un rere l'altre.

    $ tar cvf copia.tar directori/

El que fa és crear un arxiu anomenat 'copia.tar' que empaqueta tots els arxius del directori 'directori'. Un cop tenim aquest arxiu el podem copiar a una altra màquina amb qualsevol sistema i des de l'altra màquina es podrà obtenir una còpia exacta del directori amb:

   $ tar xvf copia.tar directori/

Les còpies de seguretat ocupen molt d'espai (especialment si en tenim diverses versions). Això ha portat a fer que les còpies de seguretat molt sovint no es guardin en text planer sinó que es guardin comprimides.

En sistemes Unix/Linux hi ha dos compressors per defecte 'gzip' i 'bzip2':

    $ gzip arxiu.txt
    $ ls
      arxiu.txt.gz

Com que tant gzip com bz2 només comprimeixen arxius individuals molt sovint es feien servir amb combinació amb el 'tar' i per tant el tar ja té una opció per comprimir automàticament

    $ tar cvfz copia.tar directori/	    
    $ tar cvfj copia.tar directori/

Aquest arxiu es pot passar per la xarxa amb el sistema que es vulgui: ssh, ftp, samba, etc.. Una de les formes de traspassar la informació que es fa servir a vegades és 'netcat' (nc) perquè permet copiar les dades comprimir-les, passar-les per la xarxa i descomprimir-les d'un cop:

En el servidor executem: 

    $ nc –l -p 4321 | tar xvfpz - 

En la màquina en que volem fer la còpia:

    $ tar cfzp - /directori | nc –w 3 servidor 4321 

Activitat
--------------
###Còpies de seguretat per la xarxa amb tar i ssh

1. Genereu un directori i poseu-hi alguns arxius a dins on hi hagi almenys una imatge
2. Comprimiu-lo amb 'tar' i 'gzip' i envieu-lo per la xarxa amb scp al servidor
3. Repetiu el mateix procediment amb 'bz2'
4. Elimineu el directori del vostre ordinador
5. Expliqueu el procediment que cal per recuperar la imatge de l'arxiu de la còpia de seguretat que heu fet amb els dos sistemes

###Còpies de seguretat fent servir tar i netcat

6. Genereu un directori i poseu-hi alguns arxius a dins on hi hagi almenys una imatge
7. Comprimiu-lo amb 'tar' i 'gz' i envieu-lo per la xarxa al vostre directori del servidor fent servir 'nc'
8. Elimineu la imatge
9. Expliqueu algun procediment per recuperar la imatge

###Anàlisi

10. Raoneu quin dels dos sistemes us sembla millor per fer còpies de seguretat e un lloc que necessita recuperar arxius de la còpia de seguretat sovint?


---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.3 1.6 1.7 
* Continguts 1.2 1.5 1.6 
---

###### Autor: Xavier Sala 2013.10.28 14:20:44
###### Editat per: Xavier Sala 2013.10.28 14:20:44
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
