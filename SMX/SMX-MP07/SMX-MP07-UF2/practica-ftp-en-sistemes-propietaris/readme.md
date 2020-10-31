# Pràctica FTP en Sistemes Propietaris
## SMX-MP07-UF2 - Exercici de correu electrònic i transmissió d’arxius.
#### **Pràctica FTP en Sistemes Propietaris**
*Recomanació: 
- Pràctica per tractar FTP en Windows. Utilitzarem Filezilla Server.
- Aquesta pràctica és força llarga i és per això que es aconsellable intercalar explicacions i entregues parcials de la mateixa.*

Una empresa disposa d'un Windows Server 2008 amb dues targetes de xarxa i vol instal·lar un servidor FTP Filezilla. Volen que tingui la següent configuració:

- El servei s'ha d'inicialitzar manualment. Fer que el programa d'administració s'inicïi manualment.
- No volen que puguin estar més de 2 usuaris connectats a la vegada.
- Volen personalitzar el missatge de benvinguda (utilitza el missatge que vulguis).
- Assignar un interfaz de xarxa del servidor per a rebre connexions ftp.
- Establir un rang d'ip's a les quals no se'ls permetrà connectar-se.
- Dins el rang anterior establir un rang d'ips al què sí li permetrem connectar-se.
- Permetre connexions en mode passiu a només un port (el que vulguis) i posar la ip estàtica que tinguem configurada per a connexions externes.
- No utilitzar la IP externa en connexions locals.
- Fer que l'administració estigui assignada només a un interfaz del servidor (al que no s'ha assignat l'FTP).
- Fer que s'utilitzi el port 3045 per a l'interfaz d'administració.
- Permetre només una ip per connectar-se al interfaz administrador.
- Per a cada dia, guardar un registre de les accions que realitza el servidor. Fer que els registres s'esborrin cada 10 dies.
- Establir els següents límits de baixada:
             Els dies laborables hi haurà un límit de 11 KB/s.
             Els dies no laborables hi haurà un límit de 4 KB/s.
- Establir un límit de velocitat de pujada constant de 10 kB/s
- Canviar el password d'administració.
- Crear un grup d'usuaris. Establir (C:\ftp\arrel) com a directori d'entrada per aquest grup on es tinguin permisos de lectura sobre els fitxers i de llistat sobre els directoris i subdirectoris. Cada usuari d'aquest grup ha de tenir una carpeta privada amb el seu nom i generada de forma automàtica on tindrà permís total. Aquesta carpeta es crearà dins la carpeta "C:\usuaris" però des del punt de vista de l'usuari estarà a la seva arrel i es dirà "home".
- Crear un usuari amb contrasenya dins el grup anterior.
- Permetre connexions anònimes que les envïi al directori "arrel" amb només permís de lectura i navegació per les carpetes.

Després de la configuració realitzar les accions necessàries des d'altra màquina virtual per comprovar que tots els passos anteriors s'estan aplicant correctament.
Explica tot el procés incloent captura de les pantalles.

De totes les opcions que hi ha al Filezilla i no has utilitzat n'escull una i explica què fa i com funciona.

---

#FpInfor #Smx #SmxMp07 #SmxMp07Uf02

---

###### Autor: Juaky 2014.01.10 10:37:35
###### Editat per: Juaky 2014.01.10 10:37:35
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
